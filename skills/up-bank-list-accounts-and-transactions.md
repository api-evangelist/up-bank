---
name: List Up accounts and their transactions
description: Authenticate to the Up Personal Banking API and pull accounts and transaction history, handling cursor pagination and JSON:API responses.
api: openapi/up-bank-openapi.json
operations:
  - GET /util/ping
  - GET /accounts
  - GET /accounts/{accountId}/transactions
  - GET /transactions
  - GET /transactions/{id}
---

# List Up accounts and their transactions

Read-only flow over the Up Personal Banking API (base `https://api.up.com.au/api/v1`).

## Auth
1. Obtain a Personal Access Token from the Up app or api.up.com.au.
2. Send it on every request as `Authorization: Bearer <token>`.
3. Verify it with **GET `/util/ping`** — a `200` with a `meta.id` means the token is valid; a `401` means it is missing or invalid (see the JSON:API error envelope in `errors/up-bank-problem-types.yml`).

## Steps
1. **List accounts** — **GET `/accounts`**. Optionally filter with `filter[accountType]` (`SAVER` / `TRANSACTIONAL` / `HOME_LOAN`) or `filter[ownershipType]` (`INDIVIDUAL` / `JOINT`). Each account carries `attributes.balance` (a MoneyObject) and `attributes.displayName`.
2. **List that account's transactions** — **GET `/accounts/{accountId}/transactions`** using an `id` from step 1. To scope by time, pass `filter[since]` and/or `filter[until]` (RFC 3339). Do **not** use those filters for pagination.
3. **Or list all transactions** — **GET `/transactions`** across every account; filter with `filter[status]` (`HELD` / `SETTLED`), `filter[category]`, or `filter[tag]`.
4. **Retrieve one transaction** — **GET `/transactions/{id}`** for full detail (holdInfo, roundUp, cashback, cardPurchaseMethod, foreignAmount).

## Conventions to obey
- **Pagination is cursor-based.** Set `page[size]`; then follow the opaque `links.next` URL until it is `null`. Never construct cursors by hand.
- Amounts are strings in `attributes.amount.value` plus an integer `valueInBaseUnits`; negative values are debits.
- Responses are JSON:API — read data from `data[]` / `data`, and follow `relationships[].links.related` to traverse.
- No idempotency key is needed (all operations here are reads).
