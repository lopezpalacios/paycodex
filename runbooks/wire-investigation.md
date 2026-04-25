# Runbook: cross-border wire investigation

**Scenario**: customer reports missing or delayed cross-border wire, or intermediary bank queries the payment.

## Inbound query path

1. Service receives ticket: "where is my wire?"
2. Identify UETR from customer's reference + amount + date
3. Query gpi tracker (`GET /payments/{uetr}`)
4. Tracker returns: chain progression, last-known leg + status

## Diagnosis by tracker status

| Status | Meaning | Action |
|---|---|---|
| Sent (no further updates) | Stuck at first hop | Contact correspondent IB1 |
| Pending (Pdng) | Held at some leg | Identify which bank, query for reason |
| Investigation | Bank in chain raised query | Check if SBank received query |
| Credited (Cred) | Beneficiary credited | Tell customer, share confirmation |
| Rejected (Rjct) | Failed at some leg | Identify reason, communicate, return funds |

## Outbound investigation (sending side)

1. SWIFT MT196 (legacy) or camt.029 (MX) to next-hop bank
2. Provides UETR + question
3. Receiving bank's ops responds with status
4. Iterate down chain if needed

## Common reasons for delays

- Sanctions hold (intermediary screening hit)
- Beneficiary bank KYC query (esp first payment from this counterparty)
- Bad beneficiary IBAN/account number → manual repair at last hop
- FX cutoff missed → next-day rollover
- Holiday at intermediary location

## Customer comms

- Status updates with UETR reference
- Approximate ETA based on tracker status
- Investigation case ID for follow-up

## Recall (different scenario)

- Customer wants to retrieve sent wire (e.g., wrong beneficiary)
- Send camt.056 (cancellation request) up the chain
- Cooperation-dependent — beneficiary bank may have already credited beneficiary
- Police report path for fraud cases

## Linked

[[../processes/originate-cross-border-wire]] · [[../processes/gpi-tracking]] · [[../states/cross-border-wire-lifecycle]] · [[recall-investigation]]
