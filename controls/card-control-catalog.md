# Commercial card — control catalog

| ID | Control | Frequency | Evidence | Risk |
|---|---|---|---|---|
| C-CARD-LIM-01 | Per-card + program limit enforcement | Per auth | Auth log | Excess spend |
| C-CARD-MCC-01 | MCC restriction enforcement | Per auth | Auth log | Out-of-policy spend |
| C-CARD-FRD-01 | Real-time fraud scoring on auth | Per auth | Score log | Fraud loss |
| C-CARD-3DS-01 | 3DS2 SCA on online txns | Per txn | 3DS event log | PSD2 reg |
| C-CARD-PCI-01 | PCI DSS compliance (if PAN handled) | Continuous | QSA assessment | PCI breach |
| C-CARD-DSP-01 | Chargeback within scheme window | Per dispute | Case mgmt | Loss recovery |
| C-CARD-RECN-01 | Daily clearing file reconciliation | Daily | Recon report | Settlement loss |
| C-CARD-VC-01 | Virtual card single-use enforcement | Per card | Token state | Fraud |
| C-CARD-SAN-01 | Sanctions check on cardholder + merchant | Continuous | Screening log | Reg breach |
| C-CARD-AVAIL-01 | 24/7/365 auth availability | Continuous | SLO dashboard | Customer service / scheme penalty |

## Linked

[[../concepts/card-schemes]] · [[../architecture/card-issuing-pattern]]
