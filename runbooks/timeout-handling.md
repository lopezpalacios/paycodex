# Runbook: SCT Inst timeout

**Scenario**: pacs.008 sent to CSM, no pacs.002 received within scheme timeout (10s).

## Immediate actions (automated)

1. Hub marks payment `Timeout` — internal state, NOT yet `Failed`
2. Query CSM status endpoint for UETR (where supported)
3. If CSM returns ACSC → reconcile to `Settled`
4. If CSM returns RJCT → mark `Failed`, capture reason
5. If CSM returns no record → escalate to L2

## Why ambiguous

Three possible truths under timeout:

- (A) CSM never received our request — safe to retry with same UETR
- (B) CSM received, settled, response lost — retry would double-settle (CSM dedupes by UETR)
- (C) CSM received, didn't settle in time — rail rejected

UETR-based idempotency at CSM means retry with same UETR is safe.

## L2 actions

1. Pull UETR from logs
2. Query CSM operator dashboard / API
3. Confirm beneficiary PSP did not credit (call them if needed)
4. Either:
   - Confirm settlement happened → mark Settled
   - Confirm not settled → mark Failed, notify customer
5. Reconcile internal liquidity reservation (release if Failed)

## Customer comms

- "Payment delayed" notification at 10s timeout
- Final status notification once resolved

## Reg note

Under [[../regulations/instant-payments-regulation]], rail must respond within scheme SLA. Repeated timeouts = operational issue, possible incident report.

## Linked

[[../states/payment-lifecycle]] · [[../data/pacs-002-status]]
