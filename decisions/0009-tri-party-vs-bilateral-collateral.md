# ADR 0009 — Tri-party vs bilateral collateral mgmt for repo

**Status**: Proposed
**Date**: 2026-04-25
**Deciders**: Treasurer, Repo desk, Risk

## Context

Treasury operates [[../concepts/repo]] for short-term liquidity. Two collateral mgmt models:

1. **Bilateral** — counterparties manage collateral directly
2. **Tri-party** — agent (CSD) manages collateral selection + substitution + margin

Volume-driven decision.

## Options

### A. All bilateral

- Pros: cheap, control, no agent fee
- Cons: ops burden (margin calls, substitution, mark-to-market), counterparty risk concentration

### B. All tri-party (Euroclear / Clearstream)

- Pros: ops outsourced, automated mgmt, risk reduced
- Cons: agent fees, only standardized collateral baskets
- Examples: Euroclear Collateral Highway, Clearstream Global Liquidity Hub

### C. Hybrid: tri-party for active, bilateral for tactical

- Pros: best fit per use case
- Cons: two ops models

## Decision

**C. Hybrid.** Tri-party for ongoing financing relationships (>€100M outstanding); bilateral for ad-hoc / specific collateral.

## Reasoning

- Tri-party covers 80%+ of repo volume in EU at G-SIBs
- Bilateral retained for niche cases where bespoke collateral matters
- Both [[../operators/euroclear]] + [[../operators/clearstream]] supported via T2S link

## Linked

[[../concepts/repo]] · [[../operators/euroclear]] · [[../operators/clearstream]] · [[../regulations/emir]]
