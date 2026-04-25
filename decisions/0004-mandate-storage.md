# ADR 0004 — Mandate storage architecture

**Status**: Proposed
**Date**: 2026-04-25
**Deciders**: CIO, MLRO, Payments architect

## Context

SEPA Direct Debit mandates must be retained throughout life + post-last-use audit period (Core: 14 months; local AML: up to 10 years). Storage covers signed PDFs, e-mandate evidence, plus structured metadata for fast retrieval during collection processing.

## Options

### A. All-in-OLTP (Postgres BLOBs)

- Pros: single store, transactional consistency
- Cons: bloats OLTP, expensive backups, slow restores, not designed for binary

### B. Two-tier: OLTP (metadata) + object store (documents)

- Pros: each tier optimized; object store cheap, immutable, versioned; OLTP fast for lookups
- Cons: two systems, eventual consistency window between document upload and metadata commit

### C. Vendor mandate-management product (Sirius Mandate, vendor-bundled)

- Pros: turnkey, scheme-compliance maintained by vendor
- Cons: lock-in, integration boundary, less differentiation
- Examples: in-hub modules from Volante / Form3, dedicated tools from local providers

### D. Mandate storage embedded in payment hub (single vendor)

- Pros: one system to operate
- Cons: hub vendor's storage may be limited; lift-and-shift hard later

## Decision

**B. Two-tier OLTP + object store.** Build mandate service in-house on top.

## Reasoning

- Transactional metadata in Postgres gives fast lookups during real-time collection processing
- Object store (S3 / GCS / on-prem MinIO) gives cheap immutable storage with versioning
- Decouples document lifecycle from OLTP scaling
- Easier audit + retention automation via bucket lifecycle policies

## Implementation specifics

- OLTP: Postgres, Mandate table partitioned by creation date
- Object store: KMS-encrypted (CMK per legal entity), immutable + versioned
- Two-phase commit pattern: upload doc with idempotency key → commit metadata referencing doc → on metadata fail, GC orphan via scheduled job
- Search index (Elastic / OpenSearch) for ops UI lookups by debtor IBAN, status, etc.

## Consequences

- More moving parts than option A
- Backup strategy split across OLTP + object store
- Audit needs to verify both layers in sync
- Retention automation via bucket lifecycle + OLTP scheduled job

## Linked

[[../architecture/mandate-management-pattern]] · [[../regulations/gdpr]] · [[../regulations/fadp]]
