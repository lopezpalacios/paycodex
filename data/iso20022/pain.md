# pain — Payments Initiation

Customer-to-bank messages.

| Message | Purpose | Replaces |
|---|---|---|
| pain.001 | Customer Credit Transfer Initiation | MT101 |
| pain.002 | Customer Payment Status Report | (new) |
| pain.007 | Customer Payment Reversal | (new) |
| pain.008 | Customer Direct Debit Initiation | (new) |
| pain.009 | Mandate Initiation Request | e-Mandate scheme |
| pain.010 | Mandate Amendment Request | e-Mandate scheme |
| pain.011 | Mandate Cancellation Request | e-Mandate scheme |
| pain.012 | Mandate Acceptance Report | e-Mandate scheme |
| pain.013 | Creditor Payment Activation Request | (new) |
| pain.014 | Creditor Payment Activation Response | (new) |

## Versioning

- Major: pain.001.001.X (X = ISO 20022 version)
- Currently: pain.001.001.09 (CBPR+) for cross-border, .08 for SEPA
- Per-rail rulebook may pin version

## Linked

[[../pain-001-mapping]] · [[../pain-008-mapping]] · [[pacs]]
