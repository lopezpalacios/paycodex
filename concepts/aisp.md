# AISP — Account Information Service Provider

PSD2-regulated entity that, with customer consent, accesses bank account data via APIs.

## What AISP can do

- Read account balance + transactions
- Aggregate accounts across banks
- Categorize spending
- Forecast cash flow

## Examples

- Tink (acquired by Visa)
- Plaid (US-origin, expanding EU)
- TrueLayer
- Yapily
- FinAPI
- Aggregator services for TMS / accounting

## Authentication

- Customer authenticates via own bank ([[sca-rts]] SCA)
- 90-day re-consent (extended to 180 days under recent updates)
- Consent scope: which accounts, which data

## Cash mgmt link

- Treasury aggregator using AISP to consolidate multi-bank balance + transaction data
- TMS may embed AISP capability
- Replaces / complements bank H2H feeds for some use cases

## Related

[[pisp]] · [[cbpii]] · [[../regulations/psd2-psd3]] · [[../concepts/api]]
