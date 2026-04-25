# ADR 0001 — Choose CSM for SCT Inst

**Status**: Proposed
**Date**: 2026-04-25
**Deciders**: Payments architecture, treasury sales lead, COO

## Context

We need to participate in SCT Inst before [[../regulations/instant-payments-regulation]] mandate (receive Jan 9 2025 — already past for laggards; send Oct 9 2025).

Two CSMs available: [[../concepts/tips]] (ECB) and [[../concepts/eba-rt1]] (private).

Both interoperate via TIPS bridge — full reachability either way. Question is which is primary.

## Options

### A. TIPS primary, RT1 fallback

- Pros: ECB-operated, lowest fee (€0.002 capped), ECB underwrites availability
- Cons: ECB ops mindset (vs commercial), governance via Eurosystem
- IPR-aligned: TIPS is the chosen reachability backbone

### B. RT1 primary, TIPS fallback

- Pros: Bank-owned, commercial relationship, established 2017
- Cons: higher fee, narrower reach
- Possibly chosen by banks already on RT1 with sunk integration

### C. Both primary, route by destination

- Pros: max reachability, redundancy
- Cons: double integration cost, more complex ops

## Decision

**A. TIPS primary, RT1 as fallback** for new build. Drives cost efficiency + IPR alignment.

## Consequences

- Tech: TIPS adapter primary path; RT1 adapter cold-standby
- Liquidity: TIPS Dedicated Cash Account (DCA) at ECB required
- Ops: TIPS-aligned monitoring + alerting
- Strategic: align with ECB's pan-EU instant strategy

## Linked

[[../concepts/tips]] · [[../concepts/eba-rt1]] · [[../architecture/sct-inst-physical-vendor-map]]
