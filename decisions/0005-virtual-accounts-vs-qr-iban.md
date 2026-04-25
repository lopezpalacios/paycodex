# ADR 0005 — Virtual accounts vs QR-IBAN for AR reconciliation

**Status**: Proposed
**Date**: 2026-04-25
**Deciders**: Treasury sales lead, Payments architect, AR product owner

## Context

For Swiss receivables, two strategies provide structured matching:

1. **QR-IBAN + per-invoice QRR ref** — single bank account, structured ref per invoice
2. **Virtual accounts** — virtual IBAN per customer (or per invoice), real settlement account underneath

Both deliver auto-reconciliation. Trade-offs differ.

## Options

### A. QR-IBAN + per-invoice ref only

- Pros: native CH solution, no virtual-account product needed, payer scans QR & pays
- Cons: payer's free-text payments still need fuzzy match; ref required per invoice (issuance overhead minimal)

### B. Virtual accounts only (per customer)

- Pros: any payment from that customer = auto-applied (no ref needed); cross-rail (works for SEPA, wire, not just CH)
- Cons: customer must use the right virtual IBAN; less common in CH retail; QR-bill QRR still preferable for one-off payers

### C. Hybrid: QR-IBAN+QRR for invoiced flows, virtual accounts for high-volume known customers

- Pros: best match for each scenario; covers cross-border (virtual IBAN can be EUR or CHF)
- Cons: two reconciliation paths to maintain; tenant config complexity

## Decision

**C. Hybrid.** Default to QR-bill / QRR for outbound invoicing. Offer virtual accounts as upsell for high-volume B2B customers (typically 1000+ invoices/month) and for non-CHF receivables.

## Reasoning

- QR-bill is universal in CH — payer just scans
- Virtual accounts shine for repeat B2B with predictable cadence (e.g., monthly subscription) where customer pays from same source
- Hybrid future-proofs cross-border expansion (virtual EUR IBANs for SEPA receivables)

## Implementation

- AR reconciliation engine match cascade prioritizes structured ref, falls back to VA mapping
- Tenant config flag: `va_enabled: true|false`
- Customer-facing onboarding flow for VA-eligible customers

## Consequences

- Two strategies coexist — engine must support both cleanly
- Sales motion: "premium" tier with VA, "standard" with QR-bill
- Bank product cost — VA typically charged per VA range or per match

## Linked

[[../architecture/ar-reconciliation-pattern]] · [[../concepts/virtual-accounts]] · [[../concepts/qr-bill]]
