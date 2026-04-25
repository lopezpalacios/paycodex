# In-house bank pattern

Centralized corporate treasury entity acting as internal bank for subsidiaries.

## Components

```mermaid
flowchart TB
    subgraph Subsidiaries
        S1[Subsidiary A]
        S2[Subsidiary B]
        S3[Subsidiary C]
    end

    subgraph IHB[In-House Bank]
        Ledger[(IHB Ledger)]
        Netting[Netting Engine]
        SweepEng[Sweep Engine]
        FXSvc[FX Service]
        InvestSvc[Investment Service]
    end

    subgraph External
        ExtBanks[External Banks]
        Markets[FX / MMF / Repo]
    end

    S1 -->|payment request| IHB
    S2 -->|payment request| IHB
    S3 -->|payment request| IHB
    IHB -->|net external flow| ExtBanks
    IHB --> Markets
    Netting --> Ledger
    SweepEng --> Ledger
    InvestSvc --> Markets
```

## Capabilities

- **Internal payments** — intercompany transactions netted at IHB ledger; no external bank cost
- **Payment factory** — IHB initiates external payments on behalf of subsidiaries (POBO — Payments On Behalf Of)
- **Receipts factory** — IHB receives on behalf (ROBO — Receipts On Behalf Of)
- **Netting** — multilateral netting reduces FX + payment costs
- **FX hedging** — central treasury runs hedging program
- **Investment** — central deployment of group cash
- **Tax + transfer pricing** — IHB charges subs at agreed rate

## Architecture

- **IHB Ledger** — double-entry, multi-currency, multi-entity
- **External bank gateway** — small set of bank relationships (vs each sub having its own)
- **TMS** integration — IHB is core treasury system
- **ERP** integration — subs post to IHB via shared service centre flows

## Variants

- **In-house bank lite** — netting + central FX, no POBO
- **Full IHB** — POBO/ROBO across multi-CCY multi-entity
- **Multi-entity IHB** — separate IHB per region (EMEA, APAC, Americas)

## Considerations

- Banking license? — typically not (no third-party banking activity)
- Regulatory: cross-border treasury rules (FX restrictions in some countries)
- Tax: thin capitalization, transfer pricing
- IT: integration with all sub ERPs

## Linked

[[../concepts/in-house-bank]] · [[../concepts/payment-factory]] · [[../processes/intraday-liquidity]] · [[../processes/sweep-orchestration]]
