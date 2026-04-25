# RTGS wire — control catalog (CHAPS / T2 / SIC)

| ID | Control | Frequency | Evidence | Risk |
|---|---|---|---|---|
| C-RTGS-LIQ-01 | Real-time settlement account position monitoring | Continuous | Position dashboard | Liquidity + reg |
| C-RTGS-LIQ-02 | Intraday limit alerting (floor + ceiling) | Continuous | Alert log | Liquidity |
| C-RTGS-LIQ-03 | Daily collateral pre-positioning | Daily morning | Collateral schedule | Liquidity |
| C-RTGS-SAN-01 | Per-tx sanctions screening (full screening, no IPR carve-out) | Per tx | Engine log | Sanctions breach |
| C-RTGS-CUT-01 | Cutoff awareness + customer alerting | Per tx near cutoff | Alert log | Customer service |
| C-RTGS-QUE-01 | Outbound queue prioritization correctness | Per release | Queue log | Time-critical fail |
| C-RTGS-RECN-01 | T+0 settlement account reconciliation | Daily | Recon report | Cash visibility |
| C-RTGS-RTP-01 | RTP membership compliance (CHAPS Reference Data Service, T2 ESMIG, SIC SLA) | Continuous | Membership reports | Reg breach |
| C-RTGS-DR-01 | RTGS adapter failover testing | Quarterly | DR test | DORA + reg |

## Linked

[[../regulations/dora]] · [[../processes/originate-rtgs-wire]] · [[sct-inst-control-catalog]]
