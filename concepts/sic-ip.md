# SIC IP — Swiss Instant Payments

Instant payments on SIC rail. CHF, 24/7/365, ≤10s settlement.

## Mandate timeline

- **Aug 2024** — top ~60 banks must receive
- **2026** — all banks (broader rollout)
- Driven by SNB / SIX, not market-led

## Properties

- ISO 20022 (pacs.008 inst variant)
- Limit: high (not consumer-capped like SCT Inst's €100k)
- Credit-push only
- Final + irrevocable

## Key differences vs [[sct-inst]]

- CHF only
- Single rail (SIC), no competing schemes (vs TIPS / RT1)
- Mandatory by regulation, not market choice

## Implementation challenges

- 24/7 ops — bank back-office historically batch-only
- Sanctions screening must hit <10s SLA — see [[vop]] approach in EU
- Liquidity management — funded SIC account around the clock

## Related

[[sic]] · [[sct-inst]] · [[fps]] · [[../07-risk-controls]]
