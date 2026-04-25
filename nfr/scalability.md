# NFR — Scalability

Capacity dimensions + scaling patterns.

## Dimensions

- Tx volume per second (instant rails)
- Tx volume per cycle (batch rails)
- Customer count
- Bank account count (per customer × multi-currency × multi-entity)
- Mandate count (long-lived, large)
- Statement size (large customers, monthly)

## Pattern

- **Stateless** services horizontally autoscale
- **Stateful** services partition by entity ID hash
- **Hot path** (orchestrator, screening) — vertical + horizontal, JIT compile, profile-driven optimization
- **Cold path** (reporting, recon) — batch on Spark / similar

## Capacity planning

- Peak-hour multiplier (e.g., salary day in some markets = 5-10x average)
- Year-on-year growth (5-15% typical, more for instant rails as adoption rises)
- Headroom: design at 3x peak, alert at 2x

## Database scaling

- Postgres / Aurora: vertical to ~64 vCPU, then partition
- Cockroach / Spanner: native horizontal
- Read replicas for reporting paths
- Caching for hot reads (Redis / Hazelcast)

## Linked

[[performance]] · [[../architecture/247-stack-pattern]]
