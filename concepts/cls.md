# CLS — Continuous Linked Settlement

PvP (payment-versus-payment) settlement utility for FX. Eliminates Herstatt risk (one-leg-paid risk in cross-currency settlement).

## Mechanics

- Two FX legs settled simultaneously across CLS Bank accounts at relevant central banks
- 18 eligible currencies (USD, EUR, GBP, CHF, JPY, CAD, AUD, ...)
- Settlement window: ~05:00-12:00 CET
- Net positions per currency funded by participants

## Membership

- ~70 settlement members (mostly G-SIBs)
- ~25,000+ third-party users via members
- CLS Group ownership: bank consortium

## CLS Settlement vs CLSNet vs CLSNow

- **CLS Settlement** — original PvP service
- **CLSNet** — bilateral matching + netting service for non-CLS-eligible currencies + same-day
- **CLSNow** — same-day liquidity service

## Why it matters for cash mgmt

- Treasury FX deals settle via CLS where possible
- Reduces FX settlement risk + capital charges
- Banks pre-fund net positions early in window

## Related

[[../operators/cls]] · [[../concepts/wire]] · [[nostro-vostro]]
