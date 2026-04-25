# FPS — logical architecture

Reuses [[sct-inst-logical]] core; UK-specific deltas.

## Component delta

| Component | FPS-specific |
|---|---|
| CoP Service | UK API (Pay.UK std), [[../concepts/cop]] |
| FPS Adapter | Vocalink connectivity (legacy) → NPA when live |
| Sanctions | UK OFSI primary list + global lists |
| Limit Service | £1M scheme cap enforcement, fallback to [[../concepts/chaps]] above |

## NPA preparedness

- Internal canonical format already ISO 20022-aligned (per [[payment-entity]])
- Translator to legacy FPS format isolates volatility
- When NPA goes live: swap translator, hub stays the same

## Linked

[[sct-inst-logical]] · [[../concepts/fps]] · [[../concepts/cop]]
