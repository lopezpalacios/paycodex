# Corporate actions cash flow — L3

How held securities generate cash inflows / outflows.

## Lifecycle

```mermaid
flowchart LR
    A[Issuer announces CA] --> B[CSD propagates seev.031]
    B --> C[Custodian notifies holders]
    C --> D{Optional CA?}
    D -->|yes| E[Holder elects via seev.039]
    D -->|no| F[Skip election]
    E --> G[Record date]
    F --> G
    G --> H[Payment date]
    H --> I[CSD credits / debits cash]
    I --> J[Custodian propagates]
    J --> K[Holder cash account updated]
```

## Tax handling

- Withholding at source by paying agent
- Treaty rate (DTT) applied if claim filed pre-payment
- Tax reclaim post-payment for over-withholding
- Custodian or specialist (Globe Tax, Goal Group) handles reclaims

## Cash mgmt integration

- Pre-payment: forecast inflow per known position + schedule
- Post-payment: reconcile actual vs expected
- Variance investigation:
  - Tax rate higher than expected → reclaim path
  - Position discrepancy → custodian dispute
  - Currency / FX issue
- Multi-currency: dividends in foreign CCY → FX leg

## Vendor / tech

- Custodian provides feed
- CA processing: SmartStream, Broadridge, Wave (FIS)
- Tax reclaim: Globe Tax, Goal Group, KPMG / EY services

## Related

[[../concepts/corp-actions-cash]] · [[securities-cash-leg]]
