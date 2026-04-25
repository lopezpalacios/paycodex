# Bacs R-messages — L3

R-messages = Bacs scheme messages reporting back from debtor PSP / debtor.

## Message types

| Code | Sender | Meaning |
|---|---|---|
| ARUDD | Debtor PSP | Unpaid — funds not collected |
| AUDDIS reject | Debtor PSP | New DDI cannot be set up |
| ADDACS | Debtor / PSP | DDI cancelled / amended |
| AWACS | Debtor PSP | Account amendment (e.g., new sort code post-merger) |
| DDIC | Debtor (via own PSP) | Indemnity claim under DDG |

## ARUDD reason codes

| Code | Meaning |
|---|---|
| 0 | Refer to payer |
| 1 | Instruction cancelled by payer |
| 2 | Payer deceased |
| 3 | Account transferred |
| 4 | Advance notice disputed |
| 5 | No account / wrong account number |
| 6 | No instruction held |
| 7 | Amount differs from advance notice |
| 8 | Amount not yet due |
| 9 | Presentation overdue |
| B | Account closed |

## DDIC indemnity claim

- Debtor disputes a collection
- Bank automatically refunds debtor
- Bank claims back from SU PSP (chargeback)
- SU absorbs loss + investigates

## Difference from SDD R-codes

- SDD has structured ISO 20022 R-transactions (pacs.004 with reason)
- Bacs uses scheme-specific message types
- Settlement is gross at Bacs (no netting refund mechanism like SDD pacs.004)

## Linked

[[originate-bacs-dd]] · [[../runbooks/bacs-r-message-handling]]
