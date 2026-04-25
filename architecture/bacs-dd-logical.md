# Bacs DD — logical architecture

Same shape as [[sdd-logical]], rail-specific differences.

## Differences vs SDD

| Aspect | SDD | Bacs DD |
|---|---|---|
| CSM | STEP2 / RT1 / domestic | Bacs (Vocalink) |
| Cycle | D-1 send, D settlement | Day 1/2/3 |
| Mandate registration | None scheme-wide | AUDDIS confirms at debtor PSP |
| Refund | 8 weeks Core | DDG indemnity |
| Returns | pacs.004 (ISO 20022) | ARUDD (proprietary) |
| Format | pain.008 / pacs.003 (ISO 20022) | Bacs Standard 18 (proprietary; NPA migration to ISO 20022 pending) |

## Component delta

- **AUDDIS Manager** — submit + reconcile DDI confirmations
- **DDG Claims Handler** — process DDIC chargebacks
- **Bacs Format Translator** — translate canonical Mandate + Collection to Bacs Standard 18

## Linked

[[sdd-logical]] · [[mandate-management-pattern]] · [[../concepts/bacs]]
