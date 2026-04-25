# Control: VOP — Verification of Payee

**ID**: C-VOP-01

## Description

Before initiating any SCT or SCT Inst, sending PSP must call beneficiary PSP's VOP API. Outcome logged. Override path requires explicit payer action and shifts liability.

## Trigger

Every SCT / SCT Inst initiation.

## Implementation

- See [[../architecture/vop-integration-pattern]]
- See [[../processes/vop-check-flow]]

## Evidence

- API request / response log per payment
- If override: explicit user confirmation timestamp + identity
- Logs retained per [[../regulations/gdpr]] policy

## Test cases

- Match: payment proceeds normally
- Close-match: suggestion shown, user can accept or override
- No-match: hard warning, override required
- Not-supported: informational, payment proceeds with logged status
- Timeout: scheme rule applied (proceed with logged failure)
- Beneficiary PSP unavailable: fail-safe per [[../runbooks/vop-mismatch-handling]]

## Reg mapping

- [[../regulations/instant-payments-regulation]] Art. 5c — VOP mandatory Oct 9 2025

## Linked

[[../concepts/vop]] · [[../processes/vop-check-flow]]
