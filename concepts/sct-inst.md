# SCT Inst — SEPA Instant Credit Transfer

EUR instant payment scheme. ≤10s end-to-end, 24/7/365, ≤€100k limit (raised from €15k in 2020, removed entirely under IPR for some flows).

## Mandate (Instant Payments Regulation 2024/886)

- **Receive** mandatory: Jan 9 2025 (eurozone), Jan 9 2027 (non-eurozone EU)
- **Send** mandatory: Oct 9 2025 (eurozone), Jul 9 2027 (non-eurozone EU)
- Pricing parity with [[sepa-sct]] (cannot charge premium)
- IBAN-name verification ([[vop]]) mandatory before send
- Sanctions screening shifts from per-transaction to **daily customer screening**

## Where it clears

- [[tips]] — ECB-operated, reachability backbone
- [[eba-rt1]] — competing private rail
- Cross-CSM interoperability via TIPS

## Tech requirements

- 24/7 ops, hot-hot bank back-office
- Idempotency on resends
- Pre-cached sanctions lists for <10s SLA
- Real-time fraud scoring ([[../07-risk-controls]])

## Properties

- Final + irrevocable on confirmation
- Credit-push only
- ISO 20022 (pacs.008 inst, pacs.002 status)

## Use cases

- B2B instant settlement
- Insurance claim payouts
- Salary on-demand / earned wage access
- E-commerce instant checkout

## Related

[[tips]] · [[eba-rt1]] · [[vop]] · [[../regulations/instant-payments-regulation]]
