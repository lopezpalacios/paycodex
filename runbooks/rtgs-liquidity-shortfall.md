# Runbook: RTGS liquidity shortfall

**Scenario**: outbound payment cannot settle due to insufficient settlement account balance.

## Detection

- Pre-flight check at hub: liquidity manager rejects release
- Or RTGS-side: payment queued by operator (T2 publishes `PDNG`)

## Immediate actions

1. Identify shortfall amount + currency + cutoff window
2. Check incoming pre-advices — will receipts cover within timing?
3. If yes: wait, monitor, release via queue
4. If no: act:
   - Pull from sweep account (if available)
   - Initiate intraday repo or collateralized credit at CB (T2: auto-collateralization, BoE: Reserves Account credit)
   - Borrow from group treasury (intercompany)
   - As last resort: tell customer payment will roll to next day

## Customer comms

- If time-critical: notify before cutoff, provide options
- If standard: operationally rolled, customer informed in EOD

## Post-incident

- Root cause: forecast vs actual variance, missed pre-advice
- Tune intraday liquidity buffer
- Review outgoing pacing rules

## Linked

[[../processes/originate-rtgs-wire]] · [[../architecture/rtgs-settlement-pattern]] · [[../controls/rtgs-wire-control-catalog]]
