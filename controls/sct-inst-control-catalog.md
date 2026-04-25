# SCT Inst — control catalog

Each control: ID · Description · Frequency · Evidence · Risk mitigated · Reg mapping.

| ID | Control | Frequency | Evidence | Risk | Reg |
|---|---|---|---|---|---|
| C-VOP-01 | IBAN/name verification before send | Per transaction | VOP API log + override decision | Misdirected payment | [[../regulations/instant-payments-regulation]] Art. 5c |
| C-SAN-01 | Daily customer sanctions screening | Daily + on list update | Screening run log + customer set hash | Sanctions breach | EU 2024/886 Art. 5d, [[../regulations/wtr-travel-rule]] |
| C-SAN-02 | Tx-time party screening (cached) | Per transaction | Per-payment screening result | Sanctions breach | Same |
| C-FRD-01 | Real-time fraud ML scoring | Per transaction | Score + model version + decision | Push payment fraud, BEC | [[../regulations/psd2-psd3]] |
| C-AUTH-01 | Strong Customer Authentication | Per session + transaction | SCA event log | Unauthorized payment | PSD2 RTS |
| C-LIM-01 | Per-tx + daily limit enforcement | Per transaction | Limit decision log | Excessive exposure | Bank policy |
| C-DUP-01 | Duplicate detection | Per transaction | Hash store + match log | Duplicate payment | Bank policy |
| C-IDM-01 | Idempotency on retries | Per transaction | UETR-keyed dedupe | Double settlement | Scheme |
| C-RES-01 | 24/7 availability monitoring | Continuous | Uptime + SLO dashboards | Reg + reputational | [[../regulations/dora]] |
| C-INC-01 | Major incident reporting | On incident | Incident ticket + reg notification | Reg breach | [[../regulations/dora]] |
| C-PRC-01 | Pricing parity SCT Inst vs SCT | Per pricing change | Price book + AA statement | Reg breach | IPR Art. 5b |
| C-DAT-01 | Data minimization in fraud / VOP | Continuous | DPIA + retention policy | Privacy breach | [[../regulations/gdpr]] |

## Test approach

- Unit: validation rules, idempotency, state transitions
- Integration: VOP / screening / CSM stubs
- E2E: Sandbox CSM (TIPS test environment) + simulated beneficiary
- Performance: k6 / Gatling at peak rate, p99 latency assertion
- Chaos: kill components, observe degradation

## Evidence retention

- Per [[../regulations/gdpr]] / [[../regulations/fadp]] retention rules
- Tx logs: 10 years (Swiss banking law)
- AML evidence: 10 years post-relationship
- Personal data: only as long as needed + lawful basis

## Linked

[[../07-risk-controls]] · [[../states/payment-lifecycle]]
