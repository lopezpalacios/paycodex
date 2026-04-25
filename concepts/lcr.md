# LCR — Liquidity Coverage Ratio

Basel III liquidity requirement. Bank must hold sufficient HQLA (high-quality liquid assets) to cover 30-day stress outflows.

## Formula

```
LCR = HQLA / Total net cash outflows over 30 days
LCR ≥ 100% required
```

## HQLA tiers

- **Level 1** — cash, central bank reserves, top sovereign debt (no haircut)
- **Level 2A** — high-rated corp / sovereign (15% haircut, max 40% of HQLA)
- **Level 2B** — lower-rated, equities (25-50% haircut, max 15%)

## Why cash mgmt cares

- **Operating deposits** are LCR-friendly (low outflow rate ~5-25%)
- **Non-operating deposits** are LCR-unfriendly (40-100% outflow assumption)
- Bank product design favors operating deposits — hence [[../concepts/zba]] / [[../concepts/sweep]] structures keeping balances "operational"
- Drives pricing — banks pay more for sticky deposits

## Reporting

- Daily monitoring
- Monthly LCR reporting to regulator
- Public disclosure quarterly

## Related

[[nsfr]] · [[../regulations/basel-iii]] · [[../06-pricing-revenue]]
