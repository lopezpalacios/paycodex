# SEPA Direct Debit (SDD)

EUR pull payments. Two flavors:

- **SDD Core** — retail / consumer, 8-week refund right (no questions), 13-month for unauthorized
- **SDD B2B** — between businesses, no refund right (debtor must approve mandate at their bank)

## Mandate

- Creditor obtains signed mandate (paper or e-mandate)
- Unique Mandate Reference (UMR) per mandate
- Creditor stores, refers in every collection
- See [[sepa-mandate]]

## Pre-notification

- Creditor must notify debtor before each collection (at least 14 days, can shorten by agreement)
- Often combined with invoice

## Timing

- First collection: D-5 (Core), D-1 (B2B)
- Recurrent: D-2 (Core), D-1 (B2B)
- Reduced cycles widely adopted post-rulebook 2016

## Returns / R-transactions

- R-codes per scheme (e.g., AC04 closed account, MS03 reason not specified)
- Reject, Refund, Return, Reversal, Refusal — distinct lifecycle events

## Related

[[sepa-sct]] · [[sepa-mandate]] · [[../07-risk-controls]]
