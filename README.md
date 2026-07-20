# Up (up-bank)

Up is an Australian digital-only neobank founded in 2018 as a collaboration between Melbourne software company Ferocia and Bendigo and Adelaide Bank. Up is not a mutual and is not separately licensed; it operates as a brand of ASX-listed Bendigo and Adelaide Bank, which holds the ADI licence, provides the underlying deposit products, and acquired full ownership of Ferocia and Up in 2021. Marketed as Australia's first fully cloud-hosted bank, Up serves more than one million customers through a mobile-first app. It exposes both a documented personal-banking developer API and the mandatory public CDR Product Reference Data API.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/up-bank/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/up-bank/refs/heads/main/apis.yml)

## Tags

- Financial
- Banks
- Open Banking
- CDR
- Consumer Banking
- Australia
- Neobank
- Product Reference Data

## Timestamps

- **Created:** 2026-07-20
- **Modified:** 2026-07-20

## APIs

### Up CDR Product Reference Data API

Public, unauthenticated Product Reference Data (PRD) API mandated for all Australian data holders under the Consumer Data Right. Confirmed live (HTTP 200, `x-v: 3`) returning a `data.products` array of four products (Up Everyday, Up Saver, Up Essentials Saver, Up Home Loan) with fees, rates, and eligibility. Conforms to the DSB Consumer Data Standards Banking APIs; the harvested OpenAPI is the shared CDS standard contract, not an Up-proprietary spec.

- **Human URL:** [https://consumerdatastandardsaustralia.github.io/standards/#consumer-data-standards-banking-apis](https://consumerdatastandardsaustralia.github.io/standards/#consumer-data-standards-banking-apis)
- **Base URL:** `https://api.up.com.au/cds-au/v1/banking/products`

#### Tags

- CDR
- Open Banking
- Product Reference Data
- Banking
- Australia

#### Properties

- [Documentation](https://consumerdatastandardsaustralia.github.io/standards/#get-products)
- [API Reference](https://consumerdatastandardsaustralia.github.io/standards/#consumer-data-standards-banking-apis)
- [OpenAPI](openapi/up-bank-cds-banking-products-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)

### Up Personal Banking API

Up's own documented personal-banking developer API (v1, beta), giving account holders programmatic read access to accounts and transaction data plus management of categories, tags, attachments, and webhooks for real-time transaction events. Authenticated with a Personal Access Token (Bearer) obtained in the Up app or at api.up.com.au; currently scoped to personal use. The bank-specific OpenAPI 3.0.3 contract (17 paths) is published at github.com/up-banking/api and harvested verbatim.

- **Human URL:** [https://developer.up.com.au/](https://developer.up.com.au/)
- **Base URL:** `https://api.up.com.au/api/v1`

#### Tags

- Banking
- Transactions
- Accounts
- Webhooks
- Personal Finance

#### Properties

- [Documentation](https://developer.up.com.au/)
- [API Reference](https://developer.up.com.au/#welcome)
- [OpenAPI](openapi/up-bank-openapi.json) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Source Code](https://github.com/up-banking/api)

## Common Properties

- [Website](https://www.up.com.au/)
- [Developer Portal](https://developer.up.com.au/)
- [Documentation](https://developer.up.com.au/)
- [GitHub Organization](https://github.com/up-banking)
- [LinkedIn](https://www.linkedin.com/company/upbanking/)
- [Blog](https://up.com.au/blog/)
- [Pricing](https://www.up.com.au/pricing/)
- [Terms of Service](https://up.com.au/terms-and-information/)
- [Privacy Policy](https://www.up.com.au/privacy/)
- [Support](https://up.com.au/support/)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
