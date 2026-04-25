# SCT Inst — logical architecture

Stack-agnostic component model. Each component = capability, not a vendor.

## Container view (C4 L2)

```mermaid
flowchart TB
    subgraph Channels
        Portal[Web Portal]
        API[Corp API Gateway]
        H2H[H2H SFTP]
        SWIFT[SWIFT Gateway]
    end

    subgraph Hub[Payment Hub]
        Ingest[Ingest + Validation]
        Orchestrator[Orchestrator / State Machine]
        Outbound[CSM Adapter]
        Inbound[Inbound Listener]
    end

    subgraph Services[Domain Services]
        VOPSvc[VOP Service]
        Screen[Screening Engine]
        Fraud[Fraud Engine]
        Limit[Limit Service]
        Liq[Liquidity / Position]
        Acct[Account Service]
        Notif[Notification]
    end

    subgraph Data
        TxnStore[(Transaction Store)]
        EventLog[(Event Log)]
        ScreenCache[(Screening Cache)]
        CustMaster[(Customer Master)]
    end

    subgraph External
        TIPS[TIPS / RT1]
        BenPSP[Beneficiary PSPs VOP]
        SanList[Sanctions List Providers]
    end

    Portal --> Ingest
    API --> Ingest
    H2H --> Ingest
    SWIFT --> Ingest

    Ingest --> Orchestrator
    Orchestrator <--> VOPSvc
    Orchestrator <--> Screen
    Orchestrator <--> Fraud
    Orchestrator <--> Limit
    Orchestrator <--> Liq
    Orchestrator <--> Acct
    Orchestrator --> Outbound
    Outbound --> TIPS
    TIPS --> Inbound
    Inbound --> Orchestrator
    Orchestrator --> Notif
    Orchestrator --> EventLog
    Orchestrator --> TxnStore

    VOPSvc --> BenPSP
    Screen --> ScreenCache
    Screen --> CustMaster
    SanList -.daily refresh.-> ScreenCache
```

## Component contracts

| Component | Responsibility | Stateful? | SLA |
|---|---|---|---|
| Channel Gateway | Auth, format normalize | No | <500ms |
| Ingest | Schema + duplicate check | No | <200ms |
| Orchestrator | State machine, saga | Yes | <100ms per transition |
| VOP Service | Beneficiary IBAN/name check | No (cache OK) | <2s |
| Screening | Sanctions lookup | Cache | <50ms |
| Fraud | ML scoring | No | <200ms |
| Limit | Entitlement + caps | Yes (counters) | <50ms |
| Liquidity | Reservation + release | Yes | <100ms |
| Account | Credit / debit | Yes | <100ms |
| CSM Adapter | TIPS / RT1 protocol | No (idempotent) | <2s round-trip |
| Notification | Push to corp | No | best-effort |

## Event-driven communication

- **Bus** (Kafka / Solace / RabbitMQ / Pulsar) — at-least-once
- Topics:
  - `payments.received`
  - `payments.validated`
  - `payments.screened`
  - `payments.cleared`
  - `payments.settled`
  - `payments.failed`
- Each event has paymentId + version + correlationId (UETR)
- Idempotent consumers (key by paymentId+version)

## Cross-cutting

- Auth: OIDC + mTLS internal
- Tracing: OpenTelemetry, UETR as trace ID
- Metrics: per-state SLA, per-rail volumes, error rates
- Logs: structured JSON, log-once per state transition

## Linked

[[247-stack-pattern]] · [[sct-inst-physical-vendor-map]] · [[../states/payment-lifecycle]] · [[../processes/originate-sct-inst]]
