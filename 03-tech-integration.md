# 03 — Tech Integration (CH + EU + UK)

How payment files, statements, and balances move between corp and bank.

## Channels

- Host-to-host SFTP — batch file exchange, PGP encryption
- [[concepts/swift]] — global messaging network (FIN, FileAct, gpi, SCORE for corp-to-bank)
- [[concepts/api]] — REST/JSON, OAuth2, real-time. PSD2 mandates AISP/PISP APIs in EU/UK
- Bank portal — manual web UI for treasury staff

## Formats

- [[concepts/iso-20022]] XML — pain.001, pain.002, camt.052/053/054, pacs.008
- Swiss harmonization since 2018 — pain.001 / camt.053 mandatory
- Domestic legacy formats (DTAUS DE, EFACT FR, BG-files) largely sunset under SEPA
- Legacy [[concepts/swift]] MT — being retired (cross-border MT103 → pacs.008 by Nov 2025)

## Treasury stack

- ERP (SAP S/4 HANA, Oracle, Microsoft Dynamics, Abacus CH) generates payments from invoices
- [[concepts/tms]] (Kyriba, GTreasury, FIS Quantum, Bellin / Coupa, ION) aggregates banks
- Bank API portals — UBS Connect, JPM Access, Citi CitiDirect, BofA CashPro, BNP Centric, HSBCnet, Deutsche Autobahn

## Key infra integrations

- [[concepts/qr-bill]] / [[concepts/qr-iban]] validation in CH payment factories
- [[concepts/sepa-mandate]] storage + lifecycle for SDD originators
- [[concepts/vop]] / [[concepts/cop]] APIs at point of payment initiation

## Auth / security

- SFTP: SSH keys, IP whitelist
- SWIFT: PKI, SWIFT CSP controls
- API: OAuth2, mTLS, JWT, rate limiting + PSD2 SCA / dynamic linking
- See [[07-risk-controls]] + [[regulations/dora]] resilience

## Cross-links

Output of [[01-onboarding]]. Carries traffic for [[02-products]]. Drives [[04-daily-ops]].

← [[README]]
