# VOP — Verification of Payee

IBAN-name match check before payment send. Mandated by Instant Payments Regulation 2024/886.

## Mandate dates

- Mandatory from **Oct 9 2025** for all SCT payments (not just SCT Inst)
- Must be free of charge to payer
- Applies pan-SEPA

## How it works

1. Payer initiates payment with IBAN + name
2. Sender bank queries beneficiary bank API: "is this name on this IBAN?"
3. Response: match / close-match / no-match / not-supported
4. Payer warned, decides to proceed or cancel
5. Decision logged (liability shifts on override)

## Tech

- API-based (EPC scheme rulebook)
- Sub-5s SLA expected
- Centralized routing services emerging (Surepay, iPiD, EBA Fraud Pattern and Anomaly Detection)

## Why it matters

- Anti-fraud (BEC / push payment scams)
- Liability allocation post-mandate
- Forces banks to expose name-on-account API — historic privacy debate

## Vs UK Confirmation of Payee

- UK [[cop]] rolled out 2020 — proven model VOP based on
- VOP applies pan-SEPA, CoP UK-only

## Related

[[cop]] · [[sct-inst]] · [[../regulations/instant-payments-regulation]] · [[../07-risk-controls]]
