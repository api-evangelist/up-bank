# Up (up-bank)

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

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
