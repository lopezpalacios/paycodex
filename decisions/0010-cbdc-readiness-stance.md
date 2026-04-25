# ADR 0010 — CBDC readiness stance

**Status**: Proposed
**Date**: 2026-04-25
**Deciders**: CIO, Treasurer, Innovation lead, Risk

## Context

CBDC pilots maturing. SNB Project Helvetia live since 2023 with wholesale CHF CBDC. Digital euro pending decision 2026-2027. UK + others in earlier stages.

Bank must decide investment level + posture.

## Options

### A. Wait-and-see — minimal investment

- Pros: avoid stranded investment; spec uncertain
- Cons: catch-up risk, miss early pilot learning, slow when scaling needed

### B. Active wholesale participation, watch retail

- Pros: gain experience on DLT cash-leg; SNB/SDX integration valuable; retail too uncertain to over-invest
- Cons: dual stack to maintain alongside legacy

### C. Full readiness — wholesale + retail prep

- Pros: maximum optionality
- Cons: double-counting wallet/customer experience build; high cost

## Decision

**B. Active wholesale participation, watch retail.**

## Reasoning

- Project Helvetia is live in production today — direct customer benefit available now
- Wholesale skills (DLT adapters, key mgmt, token recon) reusable for any future expansion
- Retail digital euro decision pending — premature to build full distribution wallet at scale
- Track regs + standards, build small retail PoC alongside major banks' consortia

## Implementation roadmap

1. **Now-2026**: SDX integration for tokenized bond settlement via wholesale CBDC
2. **2026**: Project Agorá / Mariana follow-on if join opportunity arises
3. **2027+**: pivot to retail digital euro distribution if go-live confirmed; reuse wallet patterns

## Linked

[[../concepts/wholesale-cbdc]] · [[../concepts/retail-cbdc]] · [[../concepts/project-helvetia]] · [[../concepts/digital-euro]] · [[../architecture/cbdc-integration-pattern]]
