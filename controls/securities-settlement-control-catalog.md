# Securities settlement — control catalog

| ID | Control | Frequency | Evidence | Risk |
|---|---|---|---|---|
| C-SS-MAT-01 | Pre-matching before sending instruction | Per instruction | Matching log | Fail risk |
| C-SS-PRE-01 | Position pre-check at counterparty side | Per instruction | Custodian feed | Fail risk |
| C-SS-DCA-01 | DCA real-time position monitoring | Continuous | Dashboard | Liquidity / fail |
| C-SS-DCA-02 | Auto-collateralization eligibility daily | Daily | Collateral schedule | Liquidity |
| C-SS-FAI-01 | Fail tracking + CSDR penalty accrual | Daily | Fail report | P&L + reg |
| C-SS-FAI-02 | Penalty reconciliation against CSD reports | Monthly | Recon report | P&L |
| C-SS-CSDR-01 | Settlement Discipline reporting | Monthly | Reg report | Reg breach |
| C-SS-CA-01 | Corp action notification within SLA | Per CA event | Distribution log | Customer service |
| C-SS-CA-02 | Corp action cash receipt vs expected | Per CA payment | Variance report | P&L + custody |
| C-SS-CA-03 | Tax reclaim filing within window | Per opportunity | Reclaim case | P&L |
| C-SS-T1-01 | T+1 readiness (post-trade affirmation by ISD-1) | Per trade | Affirmation rate | Fail risk |

## Linked

[[../regulations/csdr]] · [[../processes/securities-cash-leg]]
