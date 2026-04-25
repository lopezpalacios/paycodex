# ADR 0007 — Direct vs indirect RTGS membership

**Status**: Proposed
**Date**: 2026-04-25
**Deciders**: Treasurer, Payments architect, CFO

## Context

For each currency (CHF/EUR/GBP), bank choses direct RTGS participation or indirect via correspondent.

## Options

### A. Direct in all three (CHF/EUR/GBP)

- Pros: max control, lowest unit cost at scale, full intraday liquidity ownership
- Cons: capital + collateral burden, operational footprint, IT integration cost
- Volume threshold typically: >€1bn daily flow per currency

### B. Direct primary CCY, indirect others

- Pros: focus capital where biggest, indirect cheaper for low-volume CCYs
- Cons: indirect = correspondent dependency, less liquidity flexibility

### C. Indirect across the board

- Pros: lowest IT/integration cost, no central bank account ops
- Cons: correspondent fees, less control, dependency
- Suits smaller / focused regional banks

## Decision

**B. Direct in primary CCY (CHF for CH bank, EUR for EU bank, GBP for UK bank); indirect in non-primary.**

## Reasoning

- Direct in primary = strategic control, settlement risk minimization, pricing leverage
- Indirect in foreign CCY = right-size capital + ops to volume
- Most CH banks: direct SIC, indirect T2/CHAPS via correspondent (UBS / Commerzbank / HSBC)
- Reassess if volume in non-primary grows past threshold

## Consequences

- Foreign CCY treasury depends on correspondent SLA
- Capital allocated to primary CCY collateral pool
- Multi-rail RTGS adapter still needed (different protocols)

## Linked

[[../architecture/rtgs-settlement-pattern]] · [[0001-tips-vs-rt1]] · [[../concepts/sic]] · [[../concepts/t2]] · [[../concepts/chaps]]
