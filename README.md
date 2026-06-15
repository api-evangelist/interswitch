# Interswitch (interswitch)

Interswitch is Nigeria's foundational digital payments and transaction-switching company, founded in 2002 and regulated by the Central Bank of Nigeria. It owns the Verve card scheme (Africa's first domestic EMV chip-and-PIN brand), the Quickteller consumer and business payments platform, the Webpay / Web Checkout gateway, the Paycode cardless service, and the underlying transaction switch that connects Nigerian banks, fintechs, billers, and merchants. The Interswitch developer platform exposes REST APIs for accepting payments, sending transfers, paying bills, recharging airtime, generating cardless tokens, issuing Verve cards (Card 360), originating loans, accessing customer insights, and searching transactions — all under OAuth 2.0 client-credentials authentication via the Passport token service and HMAC-SHA512-signed webhooks. The company is expanding from Nigeria into Ghana, Kenya, Uganda, and other African markets.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/interswitch/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/interswitch/refs/heads/main/apis.yml)

## Scope

- **Position:** Producing
- **Access:** 3rd-Party

## Tags

- Payments
- Payment Infrastructure
- Card Network
- Verve
- Quickteller
- Webpay
- Bills Payment
- Transfers
- Lending
- Fintech
- Africa
- Nigeria

## Timestamps

- **Created:** 2026-05-24
- **Modified:** 2026-05-24

## APIs

### Interswitch Web Checkout API

Interswitch Web Checkout (formerly Webpay) is the company's hosted payment gateway. Two integration modes — inline JavaScript popup (`newwebpay.interswitchng.com/inline-checkout.js`) and Web Redirect form POST to `/collections/w/pay` — plus a server-side requery endpoint at `/collections/api/v1/gettransaction.json` for authoritative confirmation. Supports Verve, Visa, and Mastercard, with mandatory server-side verification before delivering value.

- **Human URL:** [https://docs.interswitchgroup.com/docs/web-checkout](https://docs.interswitchgroup.com/docs/web-checkout)

#### Tags

- Payments
- Checkout
- Webpay
- Africa
- Nigeria

#### Properties

- [Documentation](https://docs.interswitchgroup.com/docs/web-checkout)
- [Getting Started](https://docs.interswitchgroup.com/docs/quickstart)
- [OpenAPI](openapi/interswitch-web-checkout-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/interswitch-web-checkout-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/interswitch-web-checkout-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [JSON Schema](json-schema/interswitch-payment-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON-LD](json-ld/interswitch-context.jsonld) — [JSON-LD](https://www.w3.org/TR/json-ld11/)

### Interswitch Payment Gateway API

Server-to-server card payment APIs for PCI-DSS-licensed merchants — direct Card Payments, Hosted Fields, 3D Secure step-up, Google Pay, and Pay Bill payment-link generation. Base path `/paymentgateway` on the Interswitch QA/production hosts with OAuth 2.0 client_credentials authentication via the Passport token endpoint.

- **Human URL:** [https://docs.interswitchgroup.com/docs/accept-payments](https://docs.interswitchgroup.com/docs/accept-payments)

#### Tags

- Payments
- Card Payments
- Hosted Fields
- 3D Secure
- Africa

#### Properties

- [Documentation](https://docs.interswitchgroup.com/docs/accept-payments)
- [OpenAPI](openapi/interswitch-payment-gateway-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/interswitch-payment-gateway-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/interswitch-payment-gateway-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [JSON Schema](json-schema/interswitch-payment-schema.json) — [JSON Schema](https://json-schema.org/specification)

### Interswitch Transfers API

Quickteller Send Money APIs covering Single Transfer (POST /quicktellerservice/api/v5/transactions/TransferFunds), Bulk Transfer, Name Inquiry, and Bank Code Resolution. Used by banks, fintechs, and PSPs to disburse funds across NIBSS-Instant-Payment-connected Nigerian bank accounts with SHA-512 MAC authentication on each request.

- **Human URL:** [https://docs.interswitchgroup.com/docs/single-transfer](https://docs.interswitchgroup.com/docs/single-transfer)

#### Tags

- Transfers
- Payouts
- Disbursement
- Bank Transfer
- Africa

#### Properties

- [Documentation](https://docs.interswitchgroup.com/docs/single-transfer)
- [OpenAPI](openapi/interswitch-transfers-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/interswitch-transfers-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/interswitch-transfers-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Interswitch Bills Payment API

Quickteller bills payment service — list billers (`GET /api/v2/quickteller/billers`), get payment items, validate customer references, and submit payment advices for DSTV, GOTV, PHCN, water boards, school fees, government TSA payments, and hundreds of other Nigerian billers. Uses the InterswitchAuth legacy signature scheme (Authorization + Timestamp + Nonce + Signature + SignatureMethod + TerminalID headers).

- **Human URL:** [https://docs.interswitchgroup.com/docs/bills-payment](https://docs.interswitchgroup.com/docs/bills-payment)

#### Tags

- Bills
- Quickteller
- Utilities
- Cable TV
- Value Added Services
- Africa

#### Properties

- [Documentation](https://docs.interswitchgroup.com/docs/bills-payment)
- [OpenAPI](openapi/interswitch-bills-payment-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/interswitch-bills-payment-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/interswitch-bills-payment-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Interswitch Airtime Recharge API

Virtual top-up (direct airtime and data) and e-pin voucher delivery for MTN, Airtel, Glo, and 9mobile. Same biller/category/payment-item flow as Bills Payment, with category ID 4 reserved for airtime billers; phone number is supplied as `customer_id` on the `/api/v2/quickteller/payments/advices` payload.

- **Human URL:** [https://docs.interswitchgroup.com/docs/airtime-recharge](https://docs.interswitchgroup.com/docs/airtime-recharge)

#### Tags

- Airtime
- Top-up
- Virtual Top-up
- E-Pins
- Telco
- Africa

#### Properties

- [Documentation](https://docs.interswitchgroup.com/docs/airtime-recharge)
- [OpenAPI](openapi/interswitch-airtime-recharge-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/interswitch-airtime-recharge-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/interswitch-airtime-recharge-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Interswitch Paycode API

Cardless cash and merchant tokens (Pay with Mobile / Paycode). Generate single or bulk one-time tokens via `POST /api/v1/pwm/subscribers/{subscriberId}/tokens`, query token status, and cancel tokens at `/cardless-service/api/v1/cardless-services/cancel-token`. Powers ATM cardless withdrawal across the Interswitch-acquired ATM network.

- **Human URL:** [https://docs.interswitchgroup.com/docs/single-paycode](https://docs.interswitchgroup.com/docs/single-paycode)

#### Tags

- Paycode
- Cardless
- Cash Withdrawal
- Tokens
- Africa

#### Properties

- [Documentation](https://docs.interswitchgroup.com/docs/single-paycode)
- [OpenAPI](openapi/interswitch-paycode-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/interswitch-paycode-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/interswitch-paycode-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Interswitch Refunds API

Refund successful Quickteller Business transactions in full or in part via `POST /paymentgateway/api/v1/refunds`. Tracks refund lifecycle through SUCCESS, PENDING, PROCESSING, COMPLETE, COMPLETE_MANUAL, and FAILED states; auto-refunds settle T+1.

- **Human URL:** [https://docs.interswitchgroup.com/docs/refunds](https://docs.interswitchgroup.com/docs/refunds)

#### Tags

- Refunds
- Payments
- Quickteller Business
- Africa

#### Properties

- [Documentation](https://docs.interswitchgroup.com/docs/refunds)
- [OpenAPI](openapi/interswitch-refunds-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/interswitch-refunds-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/interswitch-refunds-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Interswitch Recurring Payments API

Tokenize Verve, Visa, and Mastercard cards at `POST /api/v2/purchases/validations/recurrents` then charge them on schedule via `POST /api/v2/purchases/recurrents`. Token + expiry pair replaces raw PAN so subscription merchants stay outside PCI scope.

- **Human URL:** [https://docs.interswitchgroup.com/docs/recurring-payments](https://docs.interswitchgroup.com/docs/recurring-payments)

#### Tags

- Recurring
- Subscriptions
- Tokenization
- Card On File
- Africa

#### Properties

- [Documentation](https://docs.interswitchgroup.com/docs/recurring-payments)
- [OpenAPI](openapi/interswitch-recurring-payments-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/interswitch-recurring-payments-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/interswitch-recurring-payments-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Interswitch Card 360 API

Card issuer and cardholder lifecycle management for Verve, debit, and prepaid cards — create cards, set/reset PIN, block/unblock, balance inquiry, card linking, and card validation. Lets fintechs and banks issue and operate Verve cards programmatically on the Interswitch issuer-processor.

- **Human URL:** [https://docs.interswitchgroup.com/docs/home](https://docs.interswitchgroup.com/docs/home)

#### Tags

- Cards
- Issuing
- Card Management
- Verve
- Africa

#### Properties

- [Documentation](https://docs.interswitchgroup.com/docs/home)
- [OpenAPI](openapi/interswitch-card-360-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/interswitch-card-360-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/interswitch-card-360-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Interswitch Lending API

Marketplace lending APIs connecting loan providers and distribution channels under `/lending-service/api/v1` — list providers, fetch offers (`GET /lending-service/api/v3/offers`), accept offers, fund loans, debit for repayment, and inspect customer loan status. Supports both PCI-DSS-licensed and hosted-fields integrations and powers Nano Loans, Salary Lending, and Value Financing.

- **Human URL:** [https://docs.interswitchgroup.com/docs/nano-loans](https://docs.interswitchgroup.com/docs/nano-loans)

#### Tags

- Lending
- Nano Loans
- Salary Lending
- Credit
- Africa

#### Properties

- [Documentation](https://docs.interswitchgroup.com/docs/nano-loans)
- [OpenAPI](openapi/interswitch-lending-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/interswitch-lending-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/interswitch-lending-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Interswitch Customer Insights API

Permissioned access to demography, financial history, average financial history, and financial-habit signals derived from Interswitch's transaction switch and Verve card network. Feeds credit decisioning, KYC enrichment, and segmentation for fintechs, lenders, and retail risk teams.

- **Human URL:** [https://docs.interswitchgroup.com/docs/customer-insights](https://docs.interswitchgroup.com/docs/customer-insights)

#### Tags

- Customer Insights
- Credit Decisioning
- Data
- Demographics
- Africa

#### Properties

- [Documentation](https://docs.interswitchgroup.com/docs/customer-insights)
- [OpenAPI](openapi/interswitch-customer-insights-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/interswitch-customer-insights-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/interswitch-customer-insights-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Interswitch Transaction Search API

Back-office transaction and settlement verification APIs — Quick Search, Reference Search, Bulk Search, and Transaction Detail lookups across Quickteller Business, Webpay, Transfers, and Bills Payment. Bearer-token authenticated and intended for finance, ops, and dispute teams.

- **Human URL:** [https://docs.interswitchgroup.com/docs/transaction-search](https://docs.interswitchgroup.com/docs/transaction-search)

#### Tags

- Transactions
- Search
- Settlement
- Reconciliation
- Africa

#### Properties

- [Documentation](https://docs.interswitchgroup.com/docs/transaction-search)
- [OpenAPI](openapi/interswitch-transaction-search-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/interswitch-transaction-search-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/interswitch-transaction-search-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

## Common Properties

- [Arazzo Workflows](arazzo/) — [Arazzo Specification](https://spec.openapis.org/arazzo/latest.html)
- [Portal](https://www.interswitchgroup.com)
- [Documentation](https://docs.interswitchgroup.com/docs/home)
- [Documentation](https://docs.interswitchgroup.com/reference)
- [Sign Up](https://developer.interswitchgroup.com)
- [Portal](https://developer.interswitchgroup.com/marketplace)
- [Authentication](https://docs.interswitchgroup.com/docs/authentication)
- [Authentication](https://passport-sandbox.interswitchng.com/passport/oauth/token)
- [Webhooks](https://docs.interswitchgroup.com/docs/webhooks)
- [Errors](https://docs.interswitchgroup.com/docs/response-codes)
- [Documentation](https://docs.interswitchgroup.com/llms.txt)
- [Forum](https://join.slack.com/t/iswdevelopercommunity/shared_invite/zt-2lbdgbkjq-7Byrv6unYM2nX5RwK4MQ7g)
- [Blog](https://www.interswitchgroup.com/blog)
- [Press Releases](https://www.interswitchgroup.com/news)
- [Support](https://www.interswitchgroup.com/support)
- [Careers](https://www.interswitchgroup.com/company/careers)
- [Privacy Policy](https://www.interswitchgroup.com/privacy-policy)
- [Terms of Service](https://www.interswitchgroup.com/terms-of-use)
- [Compliance](https://www.interswitchgroup.com/compliance)
- [LinkedIn](https://www.linkedin.com/company/interswitch-group)
- [Twitter](https://x.com/interswitchgrp)
- [YouTube](https://www.youtube.com/@InterswitchGroup)
- [Code Examples](https://github.com/techquest/integrating-to-ipg)
- [SDK](https://github.com/techquest/payment_php)
- [SDK](https://github.com/techquest/isw-laravel-sdk)
- [SDK](https://github.com/techquest/isw-react-sdk)
- [SDK](https://github.com/akinmail/isw-payment-sdk-android)
- [SDK](https://github.com/akinmail/isw-payment-sdk-ios)
- [Plans](plans/interswitch-plans-pricing.yml)
- [Rate Limits](rate-limits/interswitch-rate-limits.yml)
- [Fin Ops](finops/interswitch-finops.yml)
- [Vocabulary](vocabulary/interswitch-vocabulary.yml)
- [Spectral Rules](rules/interswitch-rules.yml) — [Spectral](https://docs.stoplight.io/docs/spectral)
- [Features](undefined)

## Maintainers

**FN:** Kin Lane
**Email:** info@apievangelist.com
**URL:** https://apievangelist.com
