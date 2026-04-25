# NFR — Observability

Logs, metrics, traces, audit.

## Standards

- OpenTelemetry across all services
- UETR / paymentId / customerId as universal correlation IDs
- Structured JSON logs
- W3C trace context propagation

## Metrics (RED + USE)

- Per-service: request rate, error rate, duration
- Per-resource: utilization, saturation, errors
- Business: payment success rate, sanctions hit rate, VOP override rate

## Logs

- Per-state-transition log (one record per state machine transition)
- PII masked (account numbers redacted, names hashed for analytics)
- Retained per regulatory minimum (10y CH/EU banking)

## Traces

- Sampled at edge, retained 7d in hot, 90d archived
- Critical path 100% (payment lifecycle)
- Async hops via correlationId propagation

## Audit

- Immutable audit log (append-only, signed)
- All authentication, authorization, data access
- Regulator-accessible

## Tools

- Prometheus / Grafana / Loki / Tempo
- OR Datadog / Splunk / New Relic
- ELK
- Vendor-neutral via OTel

## Linked

[[security]] · [[../regulations/dora]]
