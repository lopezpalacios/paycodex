# Runbook: sanctions hit

**Scenario**: screening engine returns hit for incoming or outgoing payment.

## Immediate actions

1. Payment moved to `Held` state — **DO NOT release**
2. Funds held in suspense account
3. Alert routed to sanctions L1 ops
4. SLA: review within scheme tolerance (sub-hour for SCT Inst — alternative is reject)

## L1 review

1. Identify hit type:
   - True positive: party matches SDN
   - False positive: similar name, different person
   - 50% rule: entity owned by SDN
2. Compare full party data: DOB, address, identifiers (BIC, IBAN, LEI)
3. Decision: clear / escalate / block

## L2 review (if escalated)

- Compliance officer reviews
- May contact regulator (especially for blocking determination)
- Document basis for decision
- If block: file SAR if suspicious, freeze funds, notify regulator

## SCT Inst constraint

Cannot complete review in 10s SLA → payment auto-rejected with RR01 (regulatory reason). Customer informed, manual investigation continues but funds never moved.

## Customer notification

- Generic "payment under review" message
- Cannot disclose sanctions hit to customer (tipping-off prohibition)

## Documentation

- Decision log per case
- Evidence retained 10y
- Quarterly trend review

## Linked

[[../controls/daily-customer-screening]] · [[../processes/sanctions-screening-flow]] · [[../regulations/amld-amlr-amla]]
