# NFR — Disaster recovery

## Targets

| Service tier | RTO | RPO |
|---|---|---|
| Instant payments | <5 min | 0 (sync replication) |
| RTGS adapter | <15 min | 0 |
| Batch rails | <2h | <5 min |
| Reporting | <4h | <1h |

## Pattern

- **Active-active across regions** for instant rails ([[../architecture/247-stack-pattern]])
- **Active-passive** for batch
- **Backup-restore** for cold reporting

## Testing

- Component-level chaos: weekly
- Regional failover: quarterly
- Full DR drill: annually
- Documented results, regulator-shared

## DORA alignment

- [[../regulations/dora]] mandates ICT incident response, recovery testing
- TLPT (Threat-Led Penetration Testing) every 3y for big firms
- Reporting major incidents to regulator within hours

## Linked

[[availability]] · [[../regulations/dora]]
