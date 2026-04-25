# Nostro / Vostro accounts

Correspondent banking accounts.

## Definitions

- **Nostro** ("ours") — our account at their bank, in their currency
- **Vostro** ("yours") — their account at our bank, in our currency

Same physical account viewed from opposite sides.

## Use

- Cross-border payments leg ([[../concepts/wire]] / [[../processes/originate-cross-border-wire]])
- Intermediate settlement in correspondent chain
- FX settlement leg (often via [[cls]])

## Management

- Daily nostro reconciliation against statements (camt.053 / MT940)
- Position limits per nostro
- Auto-funding rules
- Aging on unmatched / open items

## Tech

- Nostro recon tool: SmartStream, Broadridge, Frontier
- Near-real-time intraday: MT942 / camt.052 polling
- Drives [[../architecture/correspondent-chain-pattern]]

## Related

[[cls]] · [[../concepts/wire]] · [[../architecture/correspondent-chain-pattern]]
