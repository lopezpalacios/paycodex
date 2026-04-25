# Direct debit — SDD Core vs SDD B2B vs Bacs DD

| Aspect | [[../concepts/sepa-sdd|SDD Core]] | SDD B2B | [[../concepts/bacs|Bacs DD]] |
|---|---|---|---|
| Currency | EUR | EUR | GBP |
| Mandate | UMR per CID | UMR per CID + debtor PSP register | DDI + AUDDIS |
| First lead time | D-1 | D-1 | 10 working days |
| Recurring lead time | D-1 | D-1 | 3-day cycle |
| Refund right | 8 weeks no-q, 13m unauthorized | None | DDG (any time) |
| Pre-notification | ≥14 days (or agreed) | Same | ≥10 working days |
| Format | pain.008 / pacs.003 | Same | Bacs Standard 18 |
| Returns | pacs.004 + ISO 20022 R-codes | Same | ARUDD / ADDACS / DDIC |
| Refund / chargeback | pacs.004 (refund) | Restricted | DDIC (DDG indemnity) |
| Audit / dispute defense | Mandate evidence | Mandate + B2B confirmation | DDI + advance notice + DDG audit |

## Strategic implication

- SEPA is harmonized across 36 countries → single processing pipeline
- Bacs is UK-specific → separate engine
- DDG indemnity = creditor risk, not consumer-facing tradeoff
- B2B SDD requires registration step → onboarding cost

## Linked

[[rails-matrix]] · [[../processes/originate-sdd]] · [[../processes/originate-bacs-dd]]
