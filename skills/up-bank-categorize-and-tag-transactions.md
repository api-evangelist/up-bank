---
name: Categorize and tag Up transactions
description: Enrich Up transactions by setting their category and adding or removing user tags, respecting the categorizable and 6-tag constraints.
api: openapi/up-bank-openapi.json
operations:
  - GET /categories
  - GET /transactions/{id}
  - PATCH /transactions/{transactionId}/relationships/category
  - GET /tags
  - POST /transactions/{transactionId}/relationships/tags
  - DELETE /transactions/{transactionId}/relationships/tags
---

# Categorize and tag Up transactions

Write flow over the Up Personal Banking API. Auth is a Personal Access Token (`Authorization: Bearer <token>`).

## Categorize a transaction
1. **List categories** — **GET `/categories`** to find a valid child-category `id` (e.g. `restaurants-and-cafes`). Parent categories cannot be assigned directly.
2. **Confirm the transaction is categorizable** — **GET `/transactions/{id}`** and check `attributes.isCategorizable == true`.
3. **Set the category** — **PATCH `/transactions/{transactionId}/relationships/category`** with body `{ "data": { "type": "categories", "id": "<category-id>" } }`. To de-categorize, set the entire `data` key to `null`. Success returns **HTTP 204** (no body).

## Tag a transaction
1. **List existing tags** — **GET `/tags`** (cursor-paginated).
2. **Add tags** — **POST `/transactions/{transactionId}/relationships/tags`** with `{ "data": [ { "type": "tags", "id": "Holiday" }, ... ] }`. A transaction may hold **at most 6 tags**; duplicates are silently ignored. Success is **HTTP 204**.
3. **Remove tags** — **DELETE `/transactions/{transactionId}/relationships/tags`** with the same body shape; tags not present are silently ignored. Success is **HTTP 204**.

## Conventions to obey
- Tags are identified by their label — the label *is* the id.
- These mutations are **not idempotent** in the API (no Idempotency-Key); however, add/remove tag and set-category are naturally idempotent by outcome, so a safe retry re-sends the same body.
- Errors follow the JSON:API envelope; a `404` means the transaction, category, or tag id did not resolve.
