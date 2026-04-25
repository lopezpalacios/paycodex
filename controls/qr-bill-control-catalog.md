# QR-bill — control catalog

Controls for QR-bill issuance + AR reconciliation.

| ID | Control | Frequency | Evidence | Risk |
|---|---|---|---|---|
| C-QR-01 | Reference uniqueness per creditor | Per issuance | Registry constraint + audit | Misallocation |
| C-QR-02 | Mod-10 / Mod-97 check digit verified at issuance | Per invoice | Composer log | Invalid ref → reject by payer bank |
| C-QR-03 | IBAN-ref-type compatibility | Per invoice | Validation log | Bank-side rejection |
| C-QR-04 | QR Code rendering quality (scan test) | Per layout change | Test scan results | Payer cannot scan |
| C-AR-01 | Auto-match audit trail | Per match | Match decision log | Misallocation |
| C-AR-02 | Manual override two-eyes (over threshold) | Per override | Approval log | Internal fraud |
| C-AR-03 | Suspense balance daily zero target | Daily | Suspense aging report | Stale unmatched cash |
| C-AR-04 | Confidence score threshold tuning | Quarterly | Performance review | False-positive misallocation |
| C-AR-05 | Reconciliation completeness (settled credits = matched + suspense) | Daily | Recon report | Loss of cash visibility |
| C-EBILL-01 | eBill data sync with PDF QR data | Per issuance | Comparison log | Data divergence |
| C-PII-01 | Debtor data minimization on QR-bill | Continuous | DPIA + privacy notice | [[../regulations/fadp]] / [[../regulations/gdpr]] |
| C-RET-01 | Invoice + payment application retention | Lifecycle | Retention policy | Tax + audit |

## Test approach

- Unit: ref check digit, IBAN-ref compatibility, fuzzy match scoring
- Integration: ingestion of camt.054 → matched invoice
- E2E: issue → render PDF → scan QR → process payment → reconcile (full loop)
- Performance: bulk recon at peak (e.g., 50K credits/hour)
- Negative: malformed QR, wrong ref, partial pay, overpay, currency mismatch

## Linked

[[sct-inst-control-catalog]] · [[../states/invoice-lifecycle]] · [[../runbooks/ar-reconciliation-exceptions]]
