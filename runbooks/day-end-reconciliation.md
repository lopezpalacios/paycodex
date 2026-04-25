# Runbook: day-end reconciliation (SCT Inst)

24/7 rail makes "day-end" notional — pick local cutover (e.g., midnight CET).

## Steps

1. Pull camt.053 from CSM and from settlement bank
2. Pull internal Payment events for cutover period
3. Match: UETR + amount + currency + value date
4. Categorize:
   - Match: tick off
   - Internal-only: payment we sent, no CSM record → investigate (timeout case)
   - CSM-only: CSM has record, our system doesn't → critical, investigate
   - Amount mismatch: critical, investigate
5. Generate exception report
6. Post unrecovered breaks to suspense GL
7. Hand off to GL recon

## SLAs

- 99%+ auto-match
- Manual breaks resolved T+1
- Suspense reduced to zero T+5

## Cross-rail note

Multi-rail orgs reconcile per rail then aggregate. Use UETR as universal correlation ID.

## Linked

[[../04-daily-ops]] · [[../states/payment-lifecycle]]
