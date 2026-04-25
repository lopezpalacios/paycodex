# SDD — control catalog

Specific controls for SEPA Direct Debit collection process.

| ID | Control | Frequency | Evidence | Risk | Reg |
|---|---|---|---|---|---|
| C-MAN-01 | Mandate validity check before submission | Per collection | Mandate Service lookup log | Unauthorized debit | EPC SDD Rulebook |
| C-MAN-02 | UMR uniqueness per CID | On mandate creation | Constraint + audit | Duplicate / replay | EPC |
| C-MAN-03 | Sequence type matches mandate state | Per collection | Resolver decision log | Wrong sequence (returns) | EPC |
| C-MAN-04 | Pre-notification ≥14 days (or agreed) | Per collection batch | Creditor evidence ref | Refund right | EPC |
| C-MAN-05 | Mandate document storage immutable | Continuous | Object store policy + access log | Audit defense | Bank policy |
| C-EXP-01 | Creditor refund exposure tracked + capped | Real-time | Exposure svc state | Credit risk | Bank policy |
| C-CDT-01 | Creditor onboarding KYC + CID issuance | Per creditor | Onboarding pack | Fraud + reputational | [[../regulations/amld-amlr-amla]] |
| C-RTX-01 | R-transaction processing within scheme window | Per R-tx | Handler log + camt out | Reg breach | EPC |
| C-DUP-01 | Collection duplicate detection (UMR+date+amount) | Per submission | Hash store | Double-collect | Bank policy |
| C-PII-01 | Mandate document retention + destruction | Lifecycle | Retention policy + run log | Privacy | [[../regulations/gdpr]], [[../regulations/fadp]] |
| C-AML-01 | Creditor periodic re-screen | Daily | Screening run log | Sanctions / reputational | [[../regulations/amld-amlr-amla]] |
| C-DSP-01 | Debtor dispute SLA (response within X) | Per dispute | Case mgmt | Reg + reputational | EPC + UCITS-equivalent |

## Test approach

- Mandate state transitions covered in unit tests
- Integration: full FRST→RCUR→FNAL with mocked CSM
- E2E: scheme test environment (STEP2 sandbox)
- Performance: batch submission throughput at peak (e.g., 500K collections in window)
- Chaos: lose mandate document store mid-collection — must abort safely

## Linked

[[sct-inst-control-catalog]] · [[../states/mandate-lifecycle]] · [[../runbooks/r-transaction-handling]]
