# Intraday liquidity

Cash position management within a single business day.

## Why it matters

- Bank settlement accounts must cover outgoing throughout day
- Misalign + queue at RTGS or fail
- Costs: opportunity cost of buffer, intraday borrowing cost
- Reg: BCBS 248 (intraday liquidity monitoring tools)

## Tools

- Real-time position monitoring
- Inflow forecasting (pre-advices, predictive)
- Outflow scheduling / pacing
- Intraday credit lines (with collateral)
- Auto-funding from sweep / concentration

## Bank vs corp perspectives

- **Bank** — manages own settlement accounts at central bank, multi-CCY positions
- **Corp** — manages position at bank operating accounts, multi-bank multi-CCY

## Tech

- TMS dashboard
- Direct bank API for real-time position
- Forecasting model (ML or rule-based)
- Sweep / pooling automation

## Related

[[../concepts/sweep]] · [[../processes/intraday-liquidity]] · [[lcr]]
