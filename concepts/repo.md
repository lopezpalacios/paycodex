# Repo — Repurchase Agreement

Collateralized short-term lending. Sell securities now, agree to buy back later at higher price.

## Mechanics

- Cash lender takes securities as collateral
- Repo rate = effective interest
- Tenor: overnight to several months
- Marked-to-market collateral, daily margin calls

## Use in cash mgmt

- Treasury deploys excess cash via reverse repo (becomes collateralized lender)
- Banks fund intraday liquidity via repo (intraday with central bank or commercial)
- Money market backbone for short-term funding

## Variants

- **Bilateral** — direct between two parties
- **Tri-party** — agent (CSD) handles collateral mgmt
- **CCP-cleared** — Eurex Repo, LCH RepoClear (counterparty risk transferred to CCP)

## Margin

- Initial haircut (5-15% typical)
- Variation margin daily
- Default → cash lender liquidates collateral

## Related

[[mmf]] · [[../concepts/sweep]] · [[../regulations/emir]]
