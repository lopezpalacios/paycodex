# LC utilization (drawing) — L2

Seller presents documents, banks examine, payment flows.

## Sequence

```mermaid
sequenceDiagram
    autonumber
    participant Seller
    participant AdvBank as Advising / Negotiating Bank
    participant SWIFT
    participant IssBank as Issuing Bank
    participant Buyer

    Seller->>AdvBank: presents documents (BL, invoice, certs, etc.)
    AdvBank->>AdvBank: examine vs LC terms (ISBP 745)
    alt Compliant
        AdvBank->>SWIFT: forward docs
        SWIFT->>IssBank: docs
        IssBank->>IssBank: examine (5 banking days under UCP 600)
        IssBank-->>AdvBank: MT756 advice of payment (if compliant)
        IssBank->>AdvBank: pay (per LC terms — sight or usance)
        AdvBank-->>Seller: pay
        IssBank->>Buyer: deliver docs, debit account / draw line
    else Discrepant
        IssBank->>IssBank: identify discrepancies
        IssBank-->>AdvBank: MT734 refusal
        IssBank->>Buyer: refer for waiver?
        Buyer-->>IssBank: waive / refuse
        alt Buyer waives
            IssBank-->>AdvBank: pay anyway
        else Refuse
            IssBank-->>AdvBank: return docs / hold
        end
    end
```

## Discrepancy handling

- Common: late shipment, late presentation, missing endorsement, inconsistent data
- Issuing bank gives single notice with all discrepancies (UCP 600 art 16)
- Buyer may waive — pragmatic resolution
- If unwaived: docs returned to seller (still has goods, must find alt buyer)

## Cash leg

- Sight LC: pay on compliant presentation
- Usance LC: pay at maturity (90/180/360 days from acceptance)
- Issuing bank may discount usance bills (early pay seller, charge buyer at maturity)

## Linked

[[lc-issuance]] · [[../concepts/letter-of-credit]] · [[../concepts/ucp-600]]
