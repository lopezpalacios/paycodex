# 04 — Daily Operations (CH + EU + UK)

What corporate treasury does each day with bank cash management services.

## Morning routine (treasury analyst)

1. Pull prior-day camt.053 from all banks ([[concepts/iso-20022]])
2. Reconcile to GL — auto-match in [[concepts/tms]]
3. Cash position report = opening balance + expected in/out (per CCY)
4. Decide: invest excess (MMF, CHF/EUR time deposit) or fund shortfall (revolver draw)
5. Execute investment trade or borrowing

## Intraday

- camt.052 every 1-2 hours, or [[concepts/api]] polling
- Cutoffs:
  - [[concepts/sic]] — retail ~15:00 CET, bank-to-bank ~16:15 CET
  - [[concepts/t2]] — 18:00 CET (with extensions)
  - [[concepts/chaps]] — 18:00 GMT
  - SCT batch cutoffs — vary by CSM, often 14:00-15:00 CET for next-day settlement
- Instant rails 24/7: [[concepts/sic-ip]] · [[concepts/sct-inst]] · [[concepts/fps]]

## Payment file flow

1. ERP generates pain.001 from approved invoices
2. [[concepts/tms]] validates, applies entitlements ([[07-risk-controls]])
3. Send to bank via H2H / [[concepts/api]] / [[concepts/swift]]
4. Bank validates format, sanctions screen ([[concepts/ofac]] + EU + SECO + UK OFSI), [[concepts/vop]] / [[concepts/cop]] for credit transfers, fraud scoring
5. Bank returns pain.002 (accepted/rejected)
6. Funds debit account, send via SCT / SCT Inst / SIC / CHAPS / wire rail
7. camt.054 confirms debit

## Exceptions

- [[concepts/sepa-sdd]] R-codes: AC04 closed account, MS03 reason unknown, MD01 no mandate, etc.
- [[concepts/bacs]] returns processed end of cycle
- Wire repairs: bad beneficiary info, manual fix
- Recalls: SWIFT MT192/MT196 (legacy), pacs.028 / camt.056 (ISO 20022)
- Insufficient funds: bank decision pay-or-return based on credit limit

## End of day

- [[concepts/sweep]] runs — idle cash to investment vehicle or pay down revolver
- [[concepts/zba]] subsidiaries flatten to master
- camt.053 generated for next-morning recon
- T2 / SIC / CHAPS close-of-business cycles

## Cross-links

Service team handles exceptions ([[05-relationships]]). Volumes drive [[06-pricing-revenue]].

← [[README]]
