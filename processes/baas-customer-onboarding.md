# BaaS customer onboarding — L2

Onboarding end customer of fintech brand into sponsor bank's books.

## Flow

```mermaid
sequenceDiagram
    participant EndCust as End Customer
    participant Brand as Fintech Brand UI
    participant BaaS as BaaS Middleware
    participant Bank as Sponsor Bank
    participant KYC as KYC Provider
    participant Sanctions as Sanctions Engine

    EndCust->>Brand: signup
    Brand->>BaaS: create account request
    BaaS->>KYC: identity verification
    KYC-->>BaaS: pass / fail / refer
    BaaS->>Sanctions: screen identity
    Sanctions-->>BaaS: clear / hit
    alt Pass + clear
        BaaS->>Bank: open account (per program template)
        Bank->>Bank: assign IBAN, register customer in ledger
        Bank-->>BaaS: account ID + IBAN
        BaaS-->>Brand: account ready
        Brand-->>EndCust: welcome
    else Fail / hit
        BaaS-->>Brand: rejected with reason code
        Brand-->>EndCust: signup failed
    end
```

## Bank's responsibilities

- Final KYC sign-off (cannot fully delegate)
- AML risk rating
- Sanctions screening (own engine, not just trust BaaS)
- Reg reporting on aggregate customer base

## Brand's responsibilities

- Customer UX
- Marketing + acquisition
- L1 customer service
- Data sharing per BaaS agreement

## BaaS middleware's responsibilities

- Orchestration between brand + bank
- Common KYC vendor integration
- Customer ledger segregation
- Webhooks + real-time event distribution

## Related

[[../concepts/baas]] · [[../concepts/embedded-finance]] · [[../01-onboarding]]
