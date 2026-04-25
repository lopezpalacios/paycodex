# LC issuance — L2

End-to-end flow for issuing a documentary letter of credit.

## Sequence

```mermaid
sequenceDiagram
    autonumber
    participant Buyer
    participant IssBank as Issuing Bank
    participant Risk as Credit / Risk
    participant SWIFT
    participant AdvBank as Advising Bank
    participant Seller

    Buyer->>IssBank: LC application + commercial contract reference
    IssBank->>Risk: credit check, sanctions screening
    Risk-->>IssBank: approve / reject
    IssBank->>IssBank: collect collateral / draw credit line
    IssBank->>SWIFT: MT700 issuance
    SWIFT->>AdvBank: MT700
    AdvBank->>Seller: advice of LC
    alt Confirmation requested
        AdvBank->>AdvBank: takes risk on issuing bank, confirms
    end
    Seller->>Seller: ships goods, prepares documents
```

## Pre-issuance checks

- Buyer credit line + collateral
- Sanctions screening on all parties (incl beneficiary, applicant, vessel, ports)
- Country risk (issuing bank country, advising bank country, beneficiary country)
- Sensitive goods check (dual-use, weapons, embargoed)
- KYC on applicant + (where possible) beneficiary

## Linked

[[lc-utilization]] · [[../concepts/letter-of-credit]] · [[../concepts/ucp-600]] · [[../concepts/swift-mt-7xx]]
