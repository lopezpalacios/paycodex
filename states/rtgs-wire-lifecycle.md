# RTGS wire lifecycle (CHAPS / T2 / SIC)

```mermaid
stateDiagram-v2
    [*] --> Received
    Received --> Validated: schema + IBAN/BIC + amount
    Received --> Rejected: validation fail
    Validated --> Screened: sanctions cleared
    Validated --> Held: sanctions hit
    Screened --> LiquidityChecked: position OK
    Screened --> Queued: liquidity short, queued at RTGS
    LiquidityChecked --> Sent: pacs.008/009 to RTGS
    Queued --> Sent: liquidity arrives
    Sent --> Settled: pacs.002 ACSC from RTGS
    Sent --> Failed: rejected by RTGS
    Settled --> Reconciled: camt.054 + GL
    Held --> ManualReview
    ManualReview --> LiquidityChecked: cleared
    ManualReview --> Rejected: blocked
    Failed --> [*]
    Rejected --> [*]
    Reconciled --> [*]
```

## Differences vs SCT Inst lifecycle

- No VOP step (RTGS messages can carry VOP outcome from prior layer if used)
- Liquidity check is hard gate — RTGS will queue or reject
- Sent → Settled is operator-side, not multi-hop
- Days are not in scope — same-day settlement for all happy paths

## Linked

[[../processes/originate-rtgs-wire]] · [[payment-lifecycle]] · [[cross-border-wire-lifecycle]]
