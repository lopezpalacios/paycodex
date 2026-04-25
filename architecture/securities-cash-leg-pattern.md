# Securities cash-leg architecture pattern

Components for managing cash-leg of securities settlement.

## Logical view

```mermaid
flowchart TB
    subgraph TradingFlow
        Frontend[Front Office / OMS]
        PostTrade[Post-trade Affirmation]
    end

    subgraph SettlementHub
        InstGen[Instruction Generator]
        Matcher[Pre-matching Service]
        Sender[CSD Adapter]
        StatusListener[Status Listener]
        FailMgr[Fail Manager]
    end

    subgraph CashMgmt
        DCAMgr[DCA / Liquidity Manager]
        AutoColl[Auto-collateralization]
    end

    subgraph External
        CSD[CSD]
        T2S
        T2[T2 RTGS]
        CCP[CCP]
    end

    Frontend --> PostTrade
    PostTrade --> InstGen
    InstGen --> Matcher
    Matcher --> Sender
    Sender --> CSD
    CSD --> T2S
    T2S <--> DCAMgr
    DCAMgr <--> T2
    DCAMgr <--> AutoColl
    T2S --> StatusListener
    StatusListener --> FailMgr
    FailMgr --> Sender
    CCP --> InstGen
```

## Pre-matching service

- Compares own instruction to counterparty's published instruction
- Catches mismatches before CSD-level rejection
- Reduces failure rate
- Vendors: Bloomberg / SmartStream / DTCC ITP

## DCA / liquidity manager

- Per-currency T2S DCA (EUR primarily)
- Real-time position monitoring
- Pre-funding ahead of expected settlement waves
- Receives auto-collateralization credit on shortfall
- EOD: reconcile DCA balance, sweep back to T2 main account

## Fail manager

- Tracks Failed-state instructions
- Calculates accrued [[../concepts/csdr]] penalties
- Triggers retry on position / cash availability
- Reports fail rate + penalty cost to ops
- Liaises with counterparty CSDs for cancellation if needed

## Vendors

| Component | Build | Buy |
|---|---|---|
| Settlement hub | Often build (legacy) | SmartStream, Calypso, Murex post-trade modules |
| Pre-matching | n/a | DTCC ITP (Match), Bloomberg AIM, SmartStream Trade Process |
| DCA management | Often integrated with payment hub | T2S-certified vendors |
| Corp actions | n/a | SmartStream TLM, Broadridge |

## Linked

[[../processes/securities-cash-leg]] · [[../concepts/dvp]] · [[../concepts/t2s]] · [[../concepts/csdr]]
