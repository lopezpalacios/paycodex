# Trade finance architecture pattern

Components for issuing + servicing LC, BG, SBLC, documentary collections.

```mermaid
flowchart TB
    subgraph Bank
        TFHub[Trade Finance Hub]
        DocExam[Document Examination]
        Sanctions[Sanctions + Embargo Screening]
        CreditLink[Credit / Collateral Link]
        SWIFTGW[SWIFT Gateway]
        FeeBilling[Fee Billing]
        ContingencyTrack[Contingent Liability Tracker]
    end

    subgraph External
        Network[SWIFT Network]
        OFAC_EU_UK[Sanctions data feeds]
        DocPlatform[Doc platforms — essDOCS, Bolero, TradeLens]
    end

    Customer[Corporate Customer] --> TFHub
    TFHub --> CreditLink
    TFHub --> Sanctions
    Sanctions --> OFAC_EU_UK
    TFHub --> SWIFTGW
    SWIFTGW --> Network
    TFHub --> DocExam
    DocExam --> DocPlatform
    TFHub --> FeeBilling
    TFHub --> ContingencyTrack
```

## Components

| Component | Responsibility |
|---|---|
| Trade Finance Hub | Lifecycle mgmt for LC / BG / D/C / SBLC |
| Document Examination | OCR + rule-based discrepancy detection, manual review queue |
| Sanctions + Embargo Screening | Multi-list screening on parties + vessels + ports + commodities |
| Credit / Collateral Link | Tie issuance to credit line + collateral usage |
| SWIFT Gateway | MT 7-series messaging |
| Fee Billing | Issuance + amendment + drawing fees |
| Contingent Liability Tracker | Off-balance-sheet exposure reporting |

## Vendors

- **Trade finance platforms**: Surecomp Allnett, Finastra Trade Innovation, CGI Trade360, China Systems Eximbills
- **Document platforms**: essDOCS (electronic BL), Bolero, TradeLens (closed 2023)
- **Sanctions screening**: Fircosoft, Bridger, WorldCheck (covers vessel + dual-use lists)
- **OCR / examination**: Conpend, Surecomp DOC-X

## Integration with cash mgmt

- Drawing payment routes through [[../architecture/correspondent-chain-pattern]] for FX legs
- Settlement on day-of-pay flows via standard rails
- Fee accruals + billing tied to [[../concepts/account-analysis]]

## Linked

[[../concepts/letter-of-credit]] · [[../concepts/bank-guarantee]] · [[../processes/lc-issuance]] · [[../processes/lc-utilization]]
