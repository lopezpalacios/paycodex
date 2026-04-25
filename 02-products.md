# 02 — Product Bundle (CH + EU + UK)

What bank sells.

## Accounts

- DDA (Kontokorrent / current account) — operating account
- [[concepts/zba]] — zero balance subsidiary accounts
- Concentration accounts — pool funds across entities
- Multicurrency accounts (esp CH — native CHF/EUR/USD on single legal entity)

## Receivables

- [[concepts/qr-bill]] — Swiss invoicing standard, structured creditor reference
- [[concepts/ebill]] — Swiss e-invoicing network
- [[concepts/sepa-sdd]] — SEPA Direct Debit (Core + B2B)
- [[concepts/bacs]] Direct Debit (UK)
- [[concepts/lockbox]] — declining, mostly UK / paper-heavy industries
- [[concepts/virtual-accounts]] — auto-reconciled inbound

## Payables

- [[concepts/sepa-sct]] — batch EUR
- [[concepts/sct-inst]] — instant EUR (mandatory under IPR)
- [[concepts/sic]] payments (CHF) — single rail handles batch + RTGS
- [[concepts/sic-ip]] — Swiss instant
- [[concepts/bacs]] Direct Credit (UK batch)
- [[concepts/fps]] — UK Faster Payments
- [[concepts/wire]] — high-value RTGS ([[concepts/sic]] / [[concepts/t2]] / [[concepts/chaps]])
- Commercial card — P-card, T&E, virtual card for AP

## Liquidity

- [[concepts/sweep]] — investment sweep, loan sweep, target balancing, notional pooling
- Money market funds, repo, EUR/CHF time deposits
- Multi-currency notional pooling (legal where permitted; not US)

## FX / Trade

- Multicurrency accounts — common in CH, less in DE/FR
- FX spot, forward, swap, options for hedging (subject to [[regulations/finsa-finia]] in CH, MiFID II in EU)
- Letters of credit, documentary collections, supply chain finance

## Info reporting

- [[concepts/iso-20022]] camt.052/053/054 statements
- Real-time balance via [[concepts/api]]
- Delivered via [[03-tech-integration]] rails

## Cross-links

Used in [[01-onboarding]] to scope mandate. Priced via [[06-pricing-revenue]]. Controlled via [[07-risk-controls]].

← [[README]]
