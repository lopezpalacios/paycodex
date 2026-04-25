# Settlement instruction lifecycle (T2S DvP)

```mermaid
stateDiagram-v2
    [*] --> Created: instruction created at custodian
    Created --> Sent: sese.023 to CSD
    Sent --> Pending: at CSD, awaiting counterparty match
    Pending --> Matched: both parties' instructions matched
    Pending --> Cancelled: bilateral cancellation
    Pending --> Expired: no match by intended settlement date
    Matched --> Validated: T2S validates positions + cash
    Validated --> Settling: in atomic transfer cycle
    Validated --> Failed: insufficient securities or cash
    Settling --> Settled: sese.025 confirmation
    Failed --> Pending: retry with positions / liquidity
    Failed --> Cancelled: parties give up
    Settled --> [*]
    Cancelled --> [*]
    Expired --> [*]
```

## State semantics

| State | Owner | CSDR penalty? |
|---|---|---|
| Created | Custodian | No |
| Sent | Custodian + CSD | No |
| Pending | CSD | No (until ISD) |
| Matched | CSD | No (until ISD) |
| Validated | T2S | No |
| Settling | T2S | No |
| Settled | T2S | No |
| Failed (post-ISD) | Failing party | **Yes — cash penalty per day** |
| Cancelled | Bilateral | No |

## Penalty calculation under [[../concepts/csdr]]

- Trigger: state = Failed AND date > ISD
- Daily charge: rate × (trade value × failed period)
- Settled via CSD daily penalty mechanism
- Aggregated monthly, paid via CSD

## Linked

[[../processes/securities-cash-leg]] · [[../concepts/csdr]] · [[../data/sese-messages]]
