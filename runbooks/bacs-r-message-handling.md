# Runbook: Bacs R-message handling

**Scenario**: inbound Bacs R-message (ARUDD / ADDACS / AWACS / DDIC).

## ARUDD (unpaid)

1. Identify reason code (see [[../processes/bacs-r-messages]])
2. Reverse SU credit
3. Common reasons + actions:
   - "Insufficient funds" → re-collect attempt allowed (one retry common)
   - "Account closed" → cancel DDI (mark Cancelled)
   - "Advance notice disputed" → SU must resolve with debtor before retry
4. Notify SU
5. Track ARUDD rate per SU — high rate = SU process issue

## ADDACS (cancellation)

1. Mark DDI Cancelled
2. Block further collection attempts
3. Notify SU
4. Audit: was advance notice properly given?

## AWACS (account amendment)

1. Update DDI debtor account details
2. Continue collections under new details

## DDIC (indemnity claim)

1. Auto-refund to debtor (DDG)
2. Chargeback SU
3. Investigate: was collection authorized by valid DDI? Was advance notice given?
4. If SU at fault: SU absorbs loss
5. If bank/PSP at fault (rare): bank absorbs
6. Document trail for any subsequent dispute

## SLA

- ARUDD processing: <1 working day
- DDIC: same day refund mandatory under DDG
- Quarterly trend review

## Linked

[[../processes/bacs-r-messages]] · [[../controls/bacs-dd-control-catalog]] · [[r-transaction-handling]]
