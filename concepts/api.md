# API (Banking)

REST/JSON endpoints from bank, real-time, OAuth2.

## Common endpoints

- Balance / position (real-time)
- Transaction history
- Payment initiation (single or batch)
- FX rate / quote / execute
- Virtual account create / list ([[virtual-accounts]])
- Statement retrieval

## Standards landscape

- Open Banking UK (CMA9 mandate)
- PSD2 / PSD3 in EU
- BIAN / Berlin Group standardized models
- ISO 20022 payloads inside JSON wrappers ([[iso-20022]])

## Security

- OAuth2 / OIDC
- mTLS for client cert
- JWT signed payloads
- Rate limiting, IP allowlist
- See [[07-risk-controls]]

## Major bank platforms

- JPM Access · Citi CitiDirect · BofA CashPro · HSBCnet · Goldman TxB

## Related

[[swift]] · [[03-tech-integration]] · [[tms]]
