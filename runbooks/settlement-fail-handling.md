# Runbook: settlement fail handling

**Scenario**: settlement instruction in Failed state on or after ISD.

## Diagnose root cause

1. Check fail reason from sese.022 status
2. Common reasons:
   - **Lack of securities** (LACK_SECU)
   - **Lack of cash** (LACK_CASH)
   - **Counterparty unmatched** (UNMATCHED)
   - **Cancellation requested** (PENDING_CANC)

## Per-cause action

### LACK_SECU (our side)

- Identify why position short: failed inbound, sold short, position reservation issue
- Source securities: borrow (sec lending), buy in market
- Communicate ETA to counterparty
- Penalty accrual ongoing

### LACK_CASH (our side)

- Pre-fund DCA from main T2 account
- Trigger auto-collateralization if not already
- If chronic: review intraday liquidity forecasting

### UNMATCHED

- Compare own instruction vs counterparty version
- Common mismatches: trade price, settlement amount, counterparty agent BIC, place of settlement
- Amend via sese.027 OR coordinate with counterparty to amend

### PENDING_CANC

- One side requested cancellation
- Coordinate to confirm bilateral cancellation
- Send sese.028 if agreed

## CSDR penalty mgmt

- Penalties accrue daily until settled
- Track expected penalty cost vs cost of resolution
- Sometimes cheaper to cancel + re-trade
- Monthly: reconcile penalty payments via CSD

## SLAs

- Investigation start within 1h of fail notification
- Resolution within ISD+2 typical target
- Penalty cost monitoring monthly

## Linked

[[../processes/securities-cash-leg]] · [[../concepts/csdr]] · [[../states/settlement-instruction-lifecycle]] · [[../controls/securities-settlement-control-catalog]]
