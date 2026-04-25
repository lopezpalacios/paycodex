# Runbook: R-transaction handling

**Scenario**: inbound R-transaction (Reject / Return / Refund / Reversal) on a previously submitted SDD collection.

## Detection

- pacs.002 (pre-settlement reject) on outbound batch
- pacs.004 (return / refund / reversal) inbound from CSM
- camt.054 with R-tx amount for posting

## Actions per R-type

### Reject (pre-settlement)

1. Collection never settled
2. Mark Collection state = Rejected
3. Notify creditor with reason code
4. NO funds movement

### Return (≤5 banking days)

1. Reverse creditor credit posted at settlement
2. Mark Collection state = Returned
3. Reduce creditor's outstanding exposure tally
4. Notify creditor with reason
5. Some return reasons trigger **automatic re-collection** (e.g., AM04 NSF — creditor may re-attempt)

### Refund (8-week, Core)

1. Same as Return
2. State = Refunded
3. Refund cannot be challenged at PSP layer — debtor's right
4. Creditor pursues debtor outside payment system
5. Track refund rate per creditor — high rate = product issue

### Reversal (creditor-initiated)

1. Same as Return
2. Creditor admits error
3. May indicate process issue at creditor — escalate

### Unauthorized refund (13-month)

1. Mark state = UnauthorizedRefunded
2. Possible mandate dispute
3. Compliance review — was mandate actually valid?
4. May trigger debtor-PSP investigation request

## Customer comms

- Generic notification with reason code
- Detailed handling per creditor preference (email, file, API webhook)

## Reporting

- Daily R-rate per creditor
- Trend monitoring — sudden spike = product/process issue
- Regulatory reporting (some jurisdictions track refund rates)

## Linked

[[../processes/sdd-r-transactions]] · [[../data/r-transaction-codes]] · [[../controls/sdd-control-catalog]]
