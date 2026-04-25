# DvP — Delivery versus Payment

Settlement model where securities transfer + cash transfer happen atomically — neither leg without the other.

## Why

- Eliminates principal settlement risk (Herstatt-equivalent for securities)
- BIS standard model for post-trade

## Models (BIS DVP Models)

- **DvP Model 1** — gross-gross: each trade settles individually, simultaneous securities + cash transfer
- **DvP Model 2** — gross securities, net cash: securities settle gross, cash netted
- **DvP Model 3** — net-net: both legs netted, multilateral settlement

## On T2S

- DvP Model 1 — every trade gross-gross
- Securities and cash legs both on Eurosystem platform
- Auto-collateralization for liquidity

## On SIC + SIS (Switzerland)

- DvP via SIC cash leg + SIS securities leg
- Real-time CHF DvP

## On CREST (UK)

- DvP via Bank of England RTGS cash + CREST securities

## Related

[[t2s]] · [[csdr]] · [[../operators/euroclear]] · [[../operators/clearstream]] · [[corp-actions-cash]]
