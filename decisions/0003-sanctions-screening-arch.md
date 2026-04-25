# ADR 0003 — Sanctions screening architecture for instant rails

**Status**: Proposed
**Date**: 2026-04-25
**Deciders**: CCO, Payments architect, MLRO

## Context

[[../regulations/instant-payments-regulation]] Art. 5d allows daily customer screening for instant payments (relaxes per-tx requirement that was infeasible at 10s SLA).

We need to choose between continuing per-tx screening (slower, more thorough) and moving to daily screening (IPR-blessed, faster).

## Options

### A. Per-transaction screening (status quo)

- Pros: traditional, no architecture change
- Cons: cannot meet 10s SCT Inst SLA reliably, false-positive backlog at peak

### B. Daily customer screening + cached at-tx party check

- Pros: 10s SLA achievable, IPR-blessed
- Cons: re-architecture, requires solid customer master + delta re-screening on list update

### C. Hybrid: daily for own customers, per-tx for inbound from non-customers

- Pros: defensible — own customers known, others unknown
- Cons: complexity, two screening paths

## Decision

**B. Daily customer screening + cached at-tx party check + free-text scan.** See [[../architecture/sanctions-cache-pattern]].

## Consequences

- Tech: invest in customer master + delta re-screening pipeline
- Compliance: list update SLA tightens (must re-screen within hours)
- Ops: daily dashboard of screening completeness
- Audit: regulator expects evidence of frequency + completeness — automate evidence packs

## Risks

- New SDN published after daily run, before next refresh → window of risk. Mitigate with on-publication trigger (sub-hour delta).
- Customer changes name / structure mid-day → synchronous re-screen on update event.

## Linked

[[../controls/daily-customer-screening]] · [[../architecture/sanctions-cache-pattern]] · [[../regulations/instant-payments-regulation]]
