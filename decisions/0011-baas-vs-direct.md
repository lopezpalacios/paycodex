# ADR 0011 — Direct vs BaaS-mediated bank-fintech partnership

**Status**: Proposed
**Date**: 2026-04-25
**Deciders**: CIO, Chief Risk Officer, Head of Embedded Finance

## Context

Fintech / brand wants embedded financial products. Bank can engage:

1. **Direct bilateral** — bank builds APIs + ops to serve fintech directly
2. **Via BaaS middleware** — bank sponsors via Solaris / Unit / Bond etc.

Recent enforcement actions (2024 — Synapse, OCC consent orders) make this riskier than 2 years ago.

## Options

### A. Direct bilateral with each fintech

- Pros: tight control, full customer + program oversight, cleaner regulatory relationship
- Cons: tech investment per fintech, slower onboarding, less leverage from common platform

### B. BaaS middleware partnership

- Pros: faster onboarding, common KYC / sanctions / ops via middleware, scale
- Cons: governance gap risk, middleware can fail (Synapse), regulator skeptical
- Recent enforcement: OCC sanctions on Lineage Bank, Choice Bank, Blue Ridge Bank, Sutton Bank

### C. Build internal BaaS platform

- Pros: brand control, no third-party middleware risk, scale
- Cons: most expensive build path, 18-24mo TTM
- Pursued by Goldman, BBVA, JPMC

## Decision

**A. Direct bilateral for high-strategic-value brands; B. BaaS-via-trusted-middleware for smaller / experimental.**

## Reasoning

- Strategic brands (>$10M revenue annual / >50K customers) deserve direct engagement
- Smaller programs uneconomic for direct
- BaaS middleware: choose only top-tier, audited middleware (post-Synapse, fewer survive)
- Build internal platform if own portfolio reaches >€500M revenue / >2M customers

## Risk controls

- Per-program reconciliation daily, signed-off by ops + finance
- Quarterly compliance review of each BaaS partner
- Exit clauses + customer-money portability in every BaaS contract
- Concentration limits: no single BaaS / fintech >X% of book

## Linked

[[../concepts/baas]] · [[../concepts/embedded-finance]] · [[../architecture/baas-platform-pattern]] · [[../regulations/psd2-psd3]]
