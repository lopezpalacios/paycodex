# Card issuing architecture pattern

Components for commercial card issuing program.

```mermaid
flowchart TB
    subgraph Bank as Issuer Bank
        Hub[Card Issuing Hub]
        AuthSwitch[Authorization Switch]
        RiskEng[Real-time Risk Engine]
        TokenSvc[Token Service]
        StatementGen[Statement Generator]
        DisputeMgr[Dispute Manager]
        VirtualCardSvc[Virtual Card Service]
    end

    subgraph External
        Network[Card Network: Visa/MC/UP]
        Acquirer[Acquirer Banks]
        FraudFeed[Fraud Intel Feed]
    end

    subgraph Customer
        Corp[Corp Customer]
        ERP[Corp ERP]
    end

    Corp --> Hub
    Hub --> TokenSvc
    Hub --> VirtualCardSvc
    AuthSwitch <--> Network
    AuthSwitch --> RiskEng
    Network <--> Acquirer
    RiskEng --> FraudFeed
    Hub --> StatementGen
    StatementGen --> Corp
    Hub --> DisputeMgr
    DisputeMgr <--> Network
    StatementGen --> ERP
```

## Components

| Component | Responsibility |
|---|---|
| Card Issuing Hub | Card lifecycle (issuance, replacement, blocking), program mgmt |
| Authorization Switch | Real-time auth req/resp with networks (sub-200ms) |
| Risk Engine | Per-tx fraud + compliance check |
| Token Service | Tokenize PAN for digital wallets, virtual cards |
| Statement Generator | Cycle-based + on-demand statements, Level III data |
| Dispute Manager | Chargeback initiation + network case mgmt |
| Virtual Card Service | Issue per-use card numbers, control limits + validity |

## Vendors / outsource

- Full BaaS issuer: Marqeta, Adyen Issuing, Galileo, Stripe Issuing
- Traditional: FIS, TSYS (Global Payments), Worldline
- Specialty: Paymentology, Solaris (Germany)
- Build + scheme partnership: large incumbents

## Network connectivity

- VisaNet / Banknet / UnionPay direct connection
- Sub-second auth SLA
- 24/7/365
- DR mandatory (network-imposed)

## Related

[[../concepts/card-schemes]] · [[../concepts/commercial-card]] · [[../concepts/virtual-card]] · [[../processes/commercial-card-issuance]]
