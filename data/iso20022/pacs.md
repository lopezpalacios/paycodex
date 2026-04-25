# pacs — Payments Clearing and Settlement

Bank-to-bank messages.

| Message | Purpose | Replaces |
|---|---|---|
| pacs.002 | FI to FI Payment Status Report | (new — used in MT900/MT199 historic) |
| pacs.003 | FI to FI Customer Direct Debit | MT104 |
| pacs.004 | Payment Return | MT103 RETN / MT202 RETN |
| pacs.007 | FI to FI Payment Reversal | (new) |
| pacs.008 | FI to FI Customer Credit Transfer | MT103 |
| pacs.009 | Financial Institution Credit Transfer | MT202 / MT202 COV |
| pacs.010 | Financial Institution Direct Debit | (new) |
| pacs.028 | FI to FI Payment Status Request | (new — investigation) |

## Variants

- pacs.008 SEPA (SCT, SCT Inst)
- pacs.008 CBPR+ (cross-border)
- pacs.009 CORE (interbank)
- pacs.009 ADV (cover)

## Linked

[[../pacs-008-inst-fields]] · [[../pacs-008-cbpr-fields]] · [[../pacs-002-status]] · [[../pacs-003-fields]] · [[../pacs-009-fields]]
