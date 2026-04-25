# Cross-border wire lifecycle

State machine for one cross-border SWIFT credit transfer.

```mermaid
stateDiagram-v2
    [*] --> Received: pain.001 / MT101 received
    Received --> Validated: schema + IBAN/BIC + amount
    Received --> Rejected: validation fail
    Validated --> Screened: sanctions cleared (sender bank)
    Validated --> Held: sanctions hit
    Screened --> FXProcessed: if FX needed
    Screened --> Reserved: liquidity reserved
    FXProcessed --> Reserved
    Reserved --> Sent: pacs.008 / MT103 sent to first hop, UETR assigned
    Sent --> InTransit: status updates from gpi tracker
    InTransit --> InvestigationQueried: bank in chain raises query
    InvestigationQueried --> InTransit: query resolved
    InvestigationQueried --> Returned: cannot resolve
    InTransit --> Credited: beneficiary bank confirms
    Credited --> Reconciled: camt.054 + GL posted
    Sent --> Returned: any leg rejects or returns
    Returned --> [*]
    Reconciled --> [*]
    Held --> ManualReview
    ManualReview --> Sent: cleared
    ManualReview --> Rejected: blocked
    Rejected --> [*]
```

## State semantics

| State | Owner | Notes |
|---|---|---|
| Received | Channel Gateway | pain.001 or MT101 inbound |
| Validated | Hub | schema + business rules |
| Screened | Screening | OFAC/EU/SECO/OFSI per [[../regulations/wtr-travel-rule]] |
| FXProcessed | FX desk | rate locked, FX leg booked |
| Reserved | Liquidity | nostro reservation |
| Sent | CSM Adapter | pacs.008 to first hop, UETR registered |
| InTransit | gpi tracker | per-hop status updates |
| InvestigationQueried | Ops | manual repair / KYC at correspondent |
| Credited | Hub | beneficiary bank confirmed |
| Returned | Hub | any leg failed |
| Reconciled | Recon | camt + GL posted |

## Key differences vs SCT Inst lifecycle

- Multi-hop — `InTransit` may have multiple status updates
- Investigation possible mid-flight
- Settlement is sequential per leg, not atomic
- Days, not seconds
- Recall is real (camt.056) but cooperation-dependent

## Linked

[[../processes/originate-cross-border-wire]] · [[../processes/gpi-tracking]] · [[payment-lifecycle]]
