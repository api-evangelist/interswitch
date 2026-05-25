# Interswitch (interswitch)

Interswitch is Nigeria's foundational digital payments and transaction-switching company, founded in 2002 and regulated by the Central Bank of Nigeria. It owns the Verve card scheme (Africa's first domestic EMV chip-and-PIN brand), the Quickteller consumer and business payments platform, the Webpay / Web Checkout gateway, the Paycode cardless service, and the underlying transaction switch that connects Nigerian banks, fintechs, billers, and merchants. The Interswitch developer platform exposes REST APIs for accepting payments, sending transfers, paying bills, recharging airtime, generating cardless tokens, issuing Verve cards (Card 360), originating loans, accessing customer insights, and searching transactions.

**URL:** [Visit APIs.json](https://raw.githubusercontent.com/api-evangelist/interswitch/refs/heads/main/apis.yml)

**Run:** [Capabilities Using Naftiko](https://github.com/naftiko/fleet?utm_source=api-evangelist&utm_medium=readme&utm_campaign=company-api-evangelist&utm_content=repo)

## Tags

 - Payments, Payment Infrastructure, Card Network, Verve, Quickteller, Webpay, Bills Payment, Transfers, Lending, Fintech, Africa, Nigeria

## Timestamps

- **Created:** 2026-05-24
- **Modified:** 2026-05-24

## Authentication

Two schemes coexist on the Interswitch platform:

1. **OAuth 2.0 client_credentials (recommended).** `POST {passport}/passport/oauth/token?grant_type=client_credentials` with `Authorization: Basic base64(client_id:secret)` returns a bearer token valid for 86,400 seconds. Use `Authorization: Bearer {access_token}` on subsequent calls.
   - Sandbox: `https://passport-sandbox.interswitchng.com`
   - Production: `https://passport.interswitchng.com`
2. **InterswitchAuth (legacy).** Five headers per request: `Authorization: InterswitchAuth {base64(client_id)}`, `Timestamp`, `Nonce`, `Signature` (SHA1 of method + endpoint + timestamp + nonce + client_id + secret, base64-encoded), and `SignatureMethod: SHA1`. Plus `TerminalID` for Quickteller endpoints.

## APIs

### Interswitch Web Checkout API
Hosted payment gateway (formerly Webpay) with inline JavaScript popup and Web Redirect modes. Initiate via `POST /collections/w/pay`, then confirm authoritatively via `GET /collections/api/v1/gettransaction.json` before delivering value.

- **Human URL:** [https://docs.interswitchgroup.com/docs/web-checkout](https://docs.interswitchgroup.com/docs/web-checkout)
- [OpenAPI](openapi/interswitch-web-checkout-api-openapi.yml)
- [JSON Schema](json-schema/interswitch-payment-schema.json)
- [JSON-LD](json-ld/interswitch-context.jsonld)
- [Naftiko Capability — Payments](capabilities/web-checkout-payments.yaml)
- [Example — Inline Sandbox Payment](examples/interswitch-web-checkout-example.json)

### Interswitch Payment Gateway API
Server-to-server card payments, Hosted Fields, 3-D Secure, Google Pay, and Pay Bill payment-link generation under `/paymentgateway/api/v1`.

- **Human URL:** [https://docs.interswitchgroup.com/docs/accept-payments](https://docs.interswitchgroup.com/docs/accept-payments)
- [OpenAPI](openapi/interswitch-payment-gateway-api-openapi.yml)
- [Naftiko Capability — Payments](capabilities/payment-gateway-payments.yaml)

### Interswitch Transfers API
Quickteller Send Money — Single Transfer (`POST /quicktellerservice/api/v5/transactions/TransferFunds`), Bulk Transfer, Name Inquiry, and Bank Code Resolution over the NIBSS Instant Payment rail with SHA-512 MAC authentication.

- **Human URL:** [https://docs.interswitchgroup.com/docs/single-transfer](https://docs.interswitchgroup.com/docs/single-transfer)
- [OpenAPI](openapi/interswitch-transfers-api-openapi.yml)
- [Naftiko Capability — Transfers](capabilities/transfers-transfers.yaml)

### Interswitch Bills Payment API
Quickteller bills payment for DSTV, GOTV, PHCN, water boards, school fees, and government TSA payments via `/api/v2/quickteller/billers`, `/paymentitems`, `/customers/validations`, and `/payments/advices`.

- **Human URL:** [https://docs.interswitchgroup.com/docs/bills-payment](https://docs.interswitchgroup.com/docs/bills-payment)
- [OpenAPI](openapi/interswitch-bills-payment-api-openapi.yml)
- [Naftiko Capability — Quickteller](capabilities/bills-payment-quickteller.yaml)

### Interswitch Airtime Recharge API
Direct virtual top-up and e-pin voucher delivery for MTN, Airtel, Glo, and 9mobile via Quickteller category ID 4.

- **Human URL:** [https://docs.interswitchgroup.com/docs/airtime-recharge](https://docs.interswitchgroup.com/docs/airtime-recharge)
- [OpenAPI](openapi/interswitch-airtime-recharge-api-openapi.yml)
- [Naftiko Capability — Quickteller](capabilities/airtime-recharge-quickteller.yaml)

### Interswitch Paycode API
Cardless cash withdrawal and merchant tokens (Pay with Mobile). Single and bulk token generation, status query, and cancellation.

- **Human URL:** [https://docs.interswitchgroup.com/docs/single-paycode](https://docs.interswitchgroup.com/docs/single-paycode)
- [OpenAPI](openapi/interswitch-paycode-api-openapi.yml)
- [Naftiko Capability — Tokens](capabilities/paycode-tokens.yaml)

### Interswitch Refunds API
Full and partial refunds against successful Quickteller Business transactions at `POST /paymentgateway/api/v1/refunds`. Tracks lifecycle through SUCCESS → PROCESSING → COMPLETE.

- **Human URL:** [https://docs.interswitchgroup.com/docs/refunds](https://docs.interswitchgroup.com/docs/refunds)
- [OpenAPI](openapi/interswitch-refunds-api-openapi.yml)
- [Naftiko Capability — Refunds](capabilities/refunds-refunds.yaml)

### Interswitch Recurring Payments API
Tokenize Verve / Visa / Mastercard cards then charge them on schedule via `/api/v2/purchases/recurrents`.

- **Human URL:** [https://docs.interswitchgroup.com/docs/recurring-payments](https://docs.interswitchgroup.com/docs/recurring-payments)
- [OpenAPI](openapi/interswitch-recurring-payments-api-openapi.yml)
- [Naftiko Capability — Subscriptions](capabilities/recurring-payments-subscriptions.yaml)

### Interswitch Card 360 API
Issuer-processor card management for Verve, debit, and prepaid cards: create, get, block, unblock, set PIN, balance, link, and validate.

- **Human URL:** [https://docs.interswitchgroup.com/docs/home](https://docs.interswitchgroup.com/docs/home)
- [OpenAPI](openapi/interswitch-card-360-api-openapi.yml)
- [Naftiko Capability — Cards](capabilities/card-360-cards.yaml)

### Interswitch Lending API
Marketplace lending — list providers, fetch offers (`GET /lending-service/api/v3/offers`), accept, fund, debit, update, and inspect customer status for Nano Loans, Salary Lending, and Value Financing.

- **Human URL:** [https://docs.interswitchgroup.com/docs/nano-loans](https://docs.interswitchgroup.com/docs/nano-loans)
- [OpenAPI](openapi/interswitch-lending-api-openapi.yml)
- [Naftiko Capability — Loans](capabilities/lending-loans.yaml)

### Interswitch Customer Insights API
Permissioned access to demography, financial history, average financial history, and financial-habit signals for credit decisioning and segmentation.

- **Human URL:** [https://docs.interswitchgroup.com/docs/customer-insights](https://docs.interswitchgroup.com/docs/customer-insights)
- [OpenAPI](openapi/interswitch-customer-insights-api-openapi.yml)
- [Naftiko Capability — Insights](capabilities/customer-insights-insights.yaml)

### Interswitch Transaction Search API
Back-office Quick, Reference, Bulk, and Detail transaction lookups across the Interswitch payment surfaces.

- **Human URL:** [https://docs.interswitchgroup.com/docs/transaction-search](https://docs.interswitchgroup.com/docs/transaction-search)
- [OpenAPI](openapi/interswitch-transaction-search-api-openapi.yml)
- [Naftiko Capability — Transactions](capabilities/transaction-search-transactions.yaml)

## Cross-Cutting Artifacts

- [Plans & Pricing](plans/interswitch-plans-pricing.yml)
- [Rate Limits](rate-limits/interswitch-rate-limits.yml)
- [FinOps (FOCUS-aligned)](finops/interswitch-finops.yml)
- [Vocabulary](vocabulary/interswitch-vocabulary.yml)
- [Spectral Rules](rules/interswitch-rules.yml)
- [JSON Schema — Payment / Refund / Transfer / WebhookEvent](json-schema/interswitch-payment-schema.json)
- [JSON-LD Context](json-ld/interswitch-context.jsonld)

## Webhooks

Quickteller Business signs webhook payloads with `HmacSHA512` using the merchant's secret. The signature ships in the `X-Interswitch-Signature` header. Supported events:

- `TRANSACTION` — payment created / updated / completed
- `SUBSCRIPTION` — recurring payment created, successful charge, failed charge, cancelled
- `PAYMENT_LINKS` — payment link succeeded / failed
- `INVOICES` — invoice paid / failed

Respond `HTTP 200` immediately to acknowledge receipt; any other status triggers up to five retries.

## Developer Resources

- **Documentation:** [https://docs.interswitchgroup.com/docs/home](https://docs.interswitchgroup.com/docs/home)
- **API Reference:** [https://docs.interswitchgroup.com/reference](https://docs.interswitchgroup.com/reference)
- **Developer Console:** [https://developer.interswitchgroup.com](https://developer.interswitchgroup.com)
- **API Marketplace:** [https://developer.interswitchgroup.com/marketplace](https://developer.interswitchgroup.com/marketplace)
- **llms.txt:** [https://docs.interswitchgroup.com/llms.txt](https://docs.interswitchgroup.com/llms.txt)
- **Developer Slack:** [Join](https://join.slack.com/t/iswdevelopercommunity/shared_invite/zt-2lbdgbkjq-7Byrv6unYM2nX5RwK4MQ7g)
- **Response Codes:** [https://docs.interswitchgroup.com/docs/response-codes](https://docs.interswitchgroup.com/docs/response-codes)
