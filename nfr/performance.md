# NFR — Performance

Latency + throughput targets across hot paths.

## Latency budgets

| Operation | p50 | p95 | p99 | Hard timeout |
|---|---|---|---|---|
| [[../concepts/sct-inst]] e2e | <3s | <5s | <8s | 10s (scheme) |
| [[../concepts/sic-ip]] e2e | similar to SCT Inst | | | 10s |
| [[../concepts/fps]] e2e | <5s | <30s | <60s | 2h (scheme) |
| Sanctions cached lookup | <20ms | <50ms | <100ms | 200ms |
| [[../concepts/vop]] / [[../concepts/cop]] check | <500ms | <1.5s | <2.5s | 5s |
| Account balance read | <100ms | <300ms | <500ms | 1s |
| Payment status query | <100ms | <300ms | <500ms | 1s |

## Throughput

| Workload | Target |
|---|---|
| Outbound peak instant payments | ~5K TPS for top-10 EU bank |
| SEPA batch ingest | 1M+ items / hour during cycle |
| Statement generation | EOD batch, complete within 2h |
| API gateway | 50K RPS sustained |

## Scaling pattern

- Stateless services: horizontal autoscale on CPU + queue depth
- Stateful (orchestrator, ledger): partition by `paymentId` hash
- Hot keys (popular customer): shard further or hot-spare

## Linked

[[scalability]] · [[../architecture/247-stack-pattern]]
