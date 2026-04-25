# Cash Management Knowledge Graph — CH + EU + UK

Open-source documentation graph mapping how banks deliver cash management to corporate clients in **Switzerland, the European Union, and the United Kingdom**.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) [![Docs: CC-BY-SA-4.0](https://img.shields.io/badge/Docs-CC--BY--SA--4.0-blue.svg)](LICENSE-DOCS) [![Files](https://img.shields.io/badge/files-314-success.svg)]()

> 314 markdown files, 17 dirs, Obsidian-compatible. Cross-linked to companion graph at [`paycodex-onchain`](https://github.com/) for DLT/EVM-based equivalents.

## What this is

Stack-agnostic + vendor-aware documentation across:

- **7 sectors** — onboarding, products, tech integration, daily ops, relationships, pricing, risk
- **16 worked vertical slices** — SCT Inst, SDD, QR-bill, cross-border SWIFT/gpi, RTGS (CHAPS/T2/SIC), Bacs DD, FPS, liquidity, securities cash-leg, CBDC, cards, trade finance, BaaS, FX hedging, ESG-linked, Open Banking
- **91 concept atoms** — payment rails, services, controls, regulations, operators
- **21 regulations** with deadline tracker
- **16 operators** (CH/EU/UK supervisors + scheme operators + global utilities)
- **33 vendor profiles** — payment hubs, sanctions/fraud, TMS, core banking
- **5 cross-rail comparison matrices** — rails, direct debit, instant payments, receivables
- **NFR catalog** — availability, performance, security, scalability, observability, DR, compliance
- **ISO 20022 message catalog** — pain, pacs, camt, admi, sese
- **300+ acronym glossary**

## Quick start

```bash
# Open in Obsidian (recommended)
git clone https://github.com/lopezpalacios/paycodex
# Open the cloned directory as an Obsidian vault

# Or browse on GitHub — all linking renders in web UI

# Or use VSCode with Foam / Markdown All-in-One extensions
```

## How to read

| Persona | Start here |
|---|---|
| Newcomer | [`README.md`](README.md) → [`01-onboarding.md`](01-onboarding.md) → walk sectors |
| Engineer | Pick a vertical slice (e.g., [SCT Inst](processes/originate-sct-inst.md)) → state → entity → architecture → controls → runbook |
| Architect | [`vendors/README.md`](vendors/README.md) + [`architecture/sct-inst-physical-vendor-map.md`](architecture/sct-inst-physical-vendor-map.md) + [`decisions/`](decisions/) |
| Compliance | [`regulations/deadline-tracker.md`](regulations/deadline-tracker.md) + relevant control catalog |
| Strategist | [`comparisons/rails-matrix.md`](comparisons/rails-matrix.md) + [`EXECUTIVE-DECK.md`](EXECUTIVE-DECK.md) |

## Executive overview

See [`EXECUTIVE-DECK.md`](EXECUTIVE-DECK.md) — Marp-format slide deck.

Render to PowerPoint or PDF:

```bash
npm i -g @marp-team/marp-cli
marp EXECUTIVE-DECK.md --pptx -o exec.pptx
marp EXECUTIVE-DECK.md --pdf -o exec.pdf
```

## Companion DLT/EVM graph

[`paycodex-onchain`](https://github.com/) — same products, EVM-based DLT implementation:

- 100 ranked use cases (easy → hard)
- 24 runnable Solidity snippets (Foundry-compatible)
- 4+1 cash leg comparison (stablecoin / tokenized deposit / wholesale CBDC / retail CBDC / tokenized MMF)
- T-REX (ERC-3643) compliance patterns
- Bank integration patterns for Temenos, SAP, Oracle, Mambu, Thought Machine

## Sectors

1. **[Onboarding](01-onboarding.md)** — KYC, credit, legal, RFP
2. **[Products](02-products.md)** — accounts, receivables, payables, liquidity, FX
3. **[Tech integration](03-tech-integration.md)** — H2H, SWIFT, ISO 20022, APIs, TMS
4. **[Daily ops](04-daily-ops.md)** — morning routine, intraday, exceptions
5. **[Relationships](05-relationships.md)** — TSO, TMO, service, RM
6. **[Pricing & revenue](06-pricing-revenue.md)** — account analysis, ECR, fees
7. **[Risk & controls](07-risk-controls.md)** — entitlements, fraud, sanctions, resilience

## Worked vertical slices (full implementation depth)

Payment rails:

- [SCT Inst](processes/originate-sct-inst.md) — EUR instant
- [SDD](processes/originate-sdd.md) — SEPA Direct Debit
- [QR-bill receivables](processes/qr-bill-receivable.md) — Swiss AR reconciliation
- [Cross-border SWIFT/gpi](processes/originate-cross-border-wire.md)
- [CHAPS / T2 / SIC RTGS](processes/originate-rtgs-wire.md)
- [Bacs DD](processes/originate-bacs-dd.md) — UK direct debit
- [FPS](processes/originate-fps.md) — UK Faster Payments
- [Liquidity management](processes/intraday-liquidity.md)
- [Securities cash-leg](processes/securities-cash-leg.md) — T2S DvP
- [CBDC](processes/wholesale-cbdc-settlement.md) — wholesale + retail tracker

Adjacent product lines:

- [Cards](processes/commercial-card-issuance.md)
- [Trade finance](processes/lc-issuance.md) — LC, BG, D/C
- [Embedded finance / BaaS](processes/baas-customer-onboarding.md)
- [FX hedging](processes/fx-hedging-program.md)
- [Open Banking](architecture/open-banking-pattern.md)
- ESG-linked treasury — see [`concepts/esg-linked-loan.md`](concepts/esg-linked-loan.md)

## Regulations

[Full list with deadline tracker](regulations/deadline-tracker.md). Key:

PSD2/PSD3 · Instant Payments Regulation · WTR · AMLA · DORA · GDPR · Swiss AMLA · FinSA/FinIA · FADP · Basel III · MiFID II · EMIR · CSDR · FATCA/CRS · MiCA · Digital Euro · SFDR · CSRD · EU Taxonomy · CBDC tracker

## Reference

- [Glossary](glossary.md) — 300+ acronyms
- [Comparison matrices](comparisons/) — rails, direct debit, instant, receivables
- [ISO 20022 catalog](data/iso20022/) — pain, pacs, camt, admi, sese
- [NFR catalog](nfr/) — availability, performance, security, etc.
- [Vendor profiles](vendors/) — 33 vendors

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md). PRs welcomed for regulatory updates, new rails, vendor changes, additional patterns.

## License

- **Code** (any `.sol`, scripts) — [MIT](LICENSE)
- **Documentation** (markdown) — [CC-BY-SA-4.0](LICENSE-DOCS)
