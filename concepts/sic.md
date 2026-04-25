# SIC — Swiss Interbank Clearing

CHF RTGS. Operated by SIX Interbank Clearing AG on behalf of [[../operators/snb]].

## Properties

- Real-time gross settlement, central bank money
- All CHF interbank traffic (retail + wholesale on same rail — uncommon globally)
- Single-tier — no separate retail batch system in CH
- ISO 20022 native (since 2018 harmonization)

## Key timings (CET)

- Retail cutoff: ~15:00
- Bank-to-bank cutoff: ~16:15
- Final settlement window into evening
- Holidays follow SIX calendar

## Participants

- Swiss banks (universal, cantonal, Raiffeisen, private)
- [[postfinance]]
- Foreign banks via remote SIC access

## Adjacent

- [[sic-ip]] — instant payments overlay (mandatory rollout 2024-26)
- [[eurosic]] — EUR/CHF cross-border for Swiss banks
- [[qr-bill]] — invoicing layer feeding SIC payments

## Related

[[../operators/six]] · [[../operators/snb]] · [[../03-tech-integration]]
