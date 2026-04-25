# Runbook: AR reconciliation exceptions

**Scenario**: incoming credit cannot be auto-matched, lands in exception queue.

## Categories

### A. Wrong reference (typo / unknown)

1. Verify reference format
2. Search invoice registry by payer customer ID + amount
3. If found: confirm with customer service, manual apply
4. If not found: park in suspense, contact payer for clarification

### B. Partial payment

1. Apply portion to invoice (state → PartiallyPaid)
2. Track outstanding balance
3. Trigger reminder if no follow-up payment within window

### C. Overpayment

1. Apply full invoice amount
2. Park surplus in customer prepayment account
3. Apply to next invoice or refund per customer preference

### D. Free-text only (no structured ref)

1. Run fuzzy match (payer name + amount + date window)
2. Confidence ≥0.85 → auto-apply with manual review flag
3. Confidence <0.85 → manual queue
4. Track free-text rate per customer — high rate → push them to use ref

### E. Currency mismatch

1. Verify invoice currency vs received currency
2. If acceptable currency variant: apply with FX rate
3. Else: park in suspense, contact payer

### F. Duplicate payment

1. Detect via dedup hash (payer + amount + date + ref)
2. Hold both, customer service confirms intent
3. Refund one if true duplicate

## SLAs

- L1 review of exceptions: <24h
- Suspense aging: 0 items >5 days
- Quarterly trend review with billing operations

## Reporting

- Daily exception volume by category
- Top 10 customers by exception rate (push them to clean refs)
- Average time from credit receipt to closure

## Linked

[[../processes/ar-reconciliation]] · [[../controls/qr-bill-control-catalog]]
