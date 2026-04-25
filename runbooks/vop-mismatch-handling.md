# Runbook: VOP no-match / service failure

## Scenario A: VOP returns no-match

1. Payer sees hard warning in UI
2. Payer either cancels OR explicitly overrides
3. Override = liability shifts to payer
4. Override decision logged with timestamp + identity
5. Payment proceeds normally after override

## Scenario B: VOP timeout

- Default scheme rule: payment may proceed with logged "VOP not completed"
- Bank policy may differ — may require explicit cancellation
- Document policy, apply consistently

## Scenario C: VOP service unavailable

- Whole VOP layer down
- Options:
  - Fail open (allow payments, log "VOP unavailable") — higher fraud risk
  - Fail closed (block all SCT / SCT Inst) — service outage to customer
- Decide policy in advance, document

## Scenario D: VOP service partial outage (some BICs unreachable)

- Per-BIC fallback to "not-supported" result
- Logged for SLA tracking with VOP provider
- Escalate to vendor if persistent

## Monitoring

- VOP success rate by hour
- Latency p50, p95, p99
- Failure breakdown: timeout / 5xx / no-match / not-supported
- Provider SLA dashboard

## Linked

[[../controls/vop-control]] · [[../architecture/vop-integration-pattern]]
