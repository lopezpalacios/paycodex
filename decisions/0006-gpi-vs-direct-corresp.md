# ADR 0006 — gpi-enabled vs direct correspondent

**Status**: Proposed
**Date**: 2026-04-25
**Deciders**: Payments architect, Treasury sales, Ops lead

## Context

For cross-border wires, two integration models:

1. **gpi-enabled correspondent** — bank uses gpi-participating correspondents, posts UETR-based tracking, exposes to corp customers
2. **Direct correspondent without gpi** — older legacy chain, no UETR tracking, opaque

Most major banks now gpi-enabled. Question is whether to insist on gpi-enabled chain end-to-end.

## Options

### A. gpi-enabled chain mandatory

- Pros: real-time tracking, customer transparency, gpi SLA commitments, fewer investigations
- Cons: may force routing changes (expensive correspondents), some emerging-market beneficiary banks still non-gpi

### B. Best-effort gpi

- Pros: maximum reachability
- Cons: inconsistent customer experience, manual investigation rate higher

### C. gpi where possible + direct correspondent fallback

- Pros: pragmatic, transparency where it matters most (most volume in major-currency chains is gpi)
- Cons: bifurcated customer experience

## Decision

**C. gpi where possible + direct correspondent fallback for non-gpi destinations.**

## Reasoning

- 95%+ of typical CH/EU/UK corp cross-border volume is to gpi-enabled chains
- Forcing gpi-only would cut off some emerging-market beneficiaries
- Customer experience: gpi tracking surfaced for gpi payments; "delivery confirmation only" for non-gpi
- Sales positioning: gpi as default, fallback transparently disclosed

## Implementation

- Routing engine prefers gpi-enabled correspondents
- gpi pre-validation called for all gpi-route payments
- Customer API: gpi status surface; non-gpi shows "in transit" only
- Reporting: gpi vs non-gpi mix per quarter, trending

## Consequences

- Customer education: differentiate gpi vs non-gpi visibility
- Volume incentive: push corp to gpi destinations where alternative exists
- Vendor: SWIFT gpi membership fees + integration cost ongoing

## Linked

[[../architecture/gpi-tracker-integration]] · [[../architecture/correspondent-chain-pattern]] · [[../processes/gpi-tracking]]
