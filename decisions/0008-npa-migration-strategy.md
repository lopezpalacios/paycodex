# ADR 0008 — NPA migration readiness

**Status**: Proposed
**Date**: 2026-04-25
**Deciders**: UK Payments architect, Treasurer

## Context

UK Pay.UK is replacing FPS + Bacs with NPA (New Payments Architecture). ISO 20022 native, real-time gross settlement target. Long delayed, live date TBD.

## Options

### A. Wait for go-live, react

- Pros: less premature investment
- Cons: rush + risk when date firms up

### B. Build ISO 20022-aligned canonical now, with FPS / Bacs translators

- Pros: canonical model future-proof, switch is translator swap
- Cons: more upfront work, translator complexity for legacy

### C. Dual-track build for both legacy and NPA

- Pros: full readiness
- Cons: most expensive, doubled complexity

## Decision

**B. ISO 20022 canonical with translator pattern.**

## Reasoning

- Canonical Payment + Mandate entities are already ISO 20022-aligned across SEPA + cross-border
- Translator isolates legacy FPS / Bacs format quirks
- NPA go-live = translator-swap event, not core rebuild
- Aligns with cross-border MT→MX migration approach already in flight

## Linked

[[fps-logical]] · [[bacs-dd-logical]] · [[0002-vendor-payment-hub]]
