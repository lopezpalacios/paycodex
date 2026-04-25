# SEPA Mandate

Authorization document for [[sepa-sdd]]. Without valid mandate, debit is unauthorized → automatic refund right.

## Required fields

- Creditor identifier (CID, country-specific format)
- Unique Mandate Reference (UMR) — creditor-issued, ≤35 chars
- Debtor name + IBAN
- Type: one-off or recurrent
- Date + signature (wet or e-mandate)

## E-mandate

- e-Mandate scheme via online banking auth (limited adoption)
- Most creditors fall back to scanned PDF or signed paper

## Lifecycle

- Issued → active → first use → recurring → cancelled / amended / expired
- 36-month inactivity = mandate lapses (Core)
- Amendments tracked, UMR persists across changes (sometimes)

## Storage

- Creditor must retain mandate during life + audit period (varies by jurisdiction, often 14 months post-last-use minimum)
- Burden of proof on creditor in disputes

## Implementation note

State machine + secure document store. Frequent vendor build vs buy decision.

## Related

[[sepa-sdd]] · [[../07-risk-controls]] · [[../regulations/gdpr]]
