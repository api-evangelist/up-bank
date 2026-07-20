---
name: Receive real-time Up transaction webhooks
description: Register an Up webhook, verify its HMAC-SHA256 signature, handle transaction event types, and inspect delivery logs.
api: openapi/up-bank-openapi.json
operations:
  - POST /webhooks
  - GET /webhooks
  - GET /webhooks/{id}
  - POST /webhooks/{webhookId}/ping
  - GET /webhooks/{webhookId}/logs
  - DELETE /webhooks/{id}
---

# Receive real-time Up transaction webhooks

Event flow over the Up Personal Banking API. Auth is a Personal Access Token (`Authorization: Bearer <token>`).

## Register and test
1. **Create a webhook** — **POST `/webhooks`** with `{ "data": { "attributes": { "url": "https://your.app/up-hook", "description": "..." } } }`. The `url` must be HTTPS and <=300 chars. Success is **HTTP 201**; the response `data.attributes.secretKey` is returned **only once** — store it securely. Limit: 10 webhooks at a time.
2. **Send a test event** — **POST `/webhooks/{webhookId}/ping`** to deliver a `PING` event and confirm your endpoint is reachable.
3. **List / inspect** — **GET `/webhooks`** and **GET `/webhooks/{id}`**.

## Handle incoming events
Up POSTs JSON to your URL. Your endpoint must respond **200 within 30s** or delivery is retried with exponential backoff. Event `data.attributes.eventType` is one of:
- `TRANSACTION_CREATED` — a new transaction; follow `relationships.transaction.links.related` (i.e. GET `/transactions/{id}`) for full data.
- `TRANSACTION_SETTLED` — a HELD transaction settled.
- `TRANSACTION_DELETED` — a HELD transaction was removed (no resolvable link).
- `PING` — test event.

## Verify authenticity (required)
Every callback carries an `X-Up-Authenticity-Signature` header. Verify it:
1. Take the **raw, unparsed** request body.
2. Compute `HMAC-SHA256(secretKey, rawBody)` as a hex digest.
3. Constant-time compare against the header. Reject on mismatch.

## Debug and clean up
- **GET `/webhooks/{webhookId}/logs`** returns delivery logs (`deliveryStatus` = `DELIVERED` / `UNDELIVERABLE` / `BAD_RESPONSE_CODE`).
- **DELETE `/webhooks/{id}`** removes a webhook. If the `secretKey` is lost, delete and recreate with the same URL.

See `asyncapi/up-bank-webhooks-asyncapi.yml` for the machine-readable event surface.
