# Instant payments — SCT Inst vs SIC IP vs FPS

| Aspect | [[../concepts/sct-inst]] | [[../concepts/sic-ip]] | [[../concepts/fps]] |
|---|---|---|---|
| Currency | EUR | CHF | GBP |
| Geography | SEPA (36 countries) | CH | UK |
| SLA | <10s | <10s | <2h guaranteed (typically <10s) |
| Limit | No scheme cap (PSP discretion) | High (no consumer-style cap) | £1M scheme cap |
| Mandatory? | IPR mandate (phased 2025-27) | SIC IP rollout 2024-26 | Not mandatory but de facto for retail |
| Pre-validation | [[../concepts/vop]] mandatory Oct 2025 | None mandated | [[../concepts/cop]] mandatory |
| Settlement | TIPS / RT1 (RTGS) | SIC | FPS / Vocalink (legacy DNS); NPA (RTGS target) |
| Sanctions | Daily customer screening (IPR) | Per-bank policy, similar trend | Per-tx (continues for now) |
| APP fraud regime | Per PSD3 (in flight) | Per CH consumer law | UK PSR mandate Oct 2024 — 50/50 split |
| Pricing rule | Parity with SCT (IPR) | Market-set | Market-set |

## Common patterns

All three: 24/7/365, irrevocable, credit-push only.

## Architectural reuse

- 24/7 hot-hot pattern ([[../architecture/247-stack-pattern]]) reused across all three
- Sanctions cache pattern ([[../architecture/sanctions-cache-pattern]]) applies to all
- VOP / CoP integration pattern ([[../architecture/vop-integration-pattern]]) generalizes

## Linked

[[../processes/originate-sct-inst]] · [[../processes/originate-fps]] · [[rails-matrix]]
