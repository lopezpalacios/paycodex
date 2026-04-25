# ADR 0002 — Build vs buy: Payment Hub

**Status**: Proposed
**Date**: 2026-04-25
**Deciders**: CIO, Payments product owner, CTO

## Context

Need a multi-rail payment hub supporting SCT, SCT Inst, SDD, SIC, SIC IP, CHAPS, FPS, and cross-border SWIFT. 24/7 for instant rails.

## Options

### A. Build in-house

- Pros: full control, multi-rail abstraction tuned to ours, talent retention
- Cons: 24-36mo TTM, scarce ISO 20022 + payments engineering talent, vendor outpaces us on regulatory change

### B. Buy single-vendor hub (Volante / Form3 / Finastra / ACI / FIS)

- Pros: 6-12mo TTM, vendor handles regulatory change (IPR, CBPR+, scheme updates), proven scale
- Cons: vendor lock, customization friction, license fees, vendor's modernization timeline ≠ ours

### C. Hybrid: vendor hub + custom orchestration / channels

- Pros: vendor handles rail complexity, we own customer-facing differentiation
- Cons: integration ownership lives with us, two skill bases needed

## Decision

**C. Hybrid.** Vendor hub for rail-side (CSM adapters, message handling, scheme compliance). In-house orchestration, channel layer, customer experience, fraud/VOP integration.

## Vendor shortlist

- Volante VolPay — strong ISO 20022, instant payments certified
- Form3 — cloud-native, payments-as-a-service, fast to onboard
- Finastra Global PAYplus — broad rail coverage

## Consequences

- License cost ~€2-5M/yr depending on volume tier
- Integration patterns: REST + Kafka events
- Vendor SLA targets: 99.99% uptime, <2s p99 hub processing
- Exit strategy: data export contracts, schema portability

## Linked

[[../architecture/sct-inst-physical-vendor-map]] · [[../regulations/dora]]
