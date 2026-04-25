# Virtual card

Tokenized card number, often single-use, used for B2B payments.

## Use cases

- AP automation: each invoice gets unique virtual card number
- Online subscription mgmt: per-vendor controlled card
- Travel booking: agency-issued lodge card

## Properties

- Card number, expiry, CVV — standard format
- Limit: per-transaction or per-period cap
- Validity: minutes to months
- Single-use or multi-use
- Auto-decline above limit

## Why for AP

- Replaces ACH / wire for supplier payments
- Earns rebate (commercial card interchange)
- Enforces approval flow (issued only on approved invoice)
- Fraud-contained (unique number per use)

## Vendors

- Issuer: bank's commercial card platform (often Visa Commercial / Mastercard Smart Data)
- Platform: Conferma, AOC Solutions, Boost Payment Solutions, JPM Single-Use Account

## Settlement

- Same as standard card: merchant submits via acquirer → scheme → issuer → buyer's card account
- Buyer pays card statement on standard card terms (often net + cycle)

## Related

[[commercial-card]] · [[card-schemes]] · [[interchange]] · [[../concepts/payment-factory]]
