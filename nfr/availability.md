# NFR — Availability

Per-rail uptime targets reflecting customer + regulatory expectations.

## SLO targets

| Service | Target | Notes |
|---|---|---|
| Instant payments ([[../concepts/sct-inst]], [[../concepts/sic-ip]], [[../concepts/fps]]) | 99.99% (52 min/year max downtime) | 24/7/365 |
| RTGS rails (during business hours) | 99.95% | Cutoff windows define business hours |
| Batch rails (SEPA SCT/SDD, Bacs) | 99.9% (during processing windows) | Off-hours batch ops |
| Customer portal / [[../concepts/api]] | 99.95% | 24/7 expectation post-instant |
| Statement reporting | 99.5% | Less time-sensitive |

## Dependencies

- Single regional outage cannot breach instant SLO → multi-AZ + multi-region
- CSM operator outages: bank cannot exceed CSM uptime; design for graceful degradation
- Vendor SLAs: must back back-to-back into bank's customer SLA

## Measurement

- SLI defined per service (success rate of well-formed requests)
- Error budget tracked monthly
- Burn-rate alerting (multiple windows, multiple severities)

## Linked

[[../regulations/dora]] · [[disaster-recovery]] · [[performance]]
