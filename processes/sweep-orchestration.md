# Sweep orchestration — L3

Daily / intraday automated movement of funds between accounts.

## Sweep types

| Type | Trigger | Movement |
|---|---|---|
| Investment sweep | EOD excess above target | Concentration → MMF / repo |
| Loan sweep | EOD excess + revolver outstanding | Concentration → revolver paydown |
| Target balancing | Each cutoff | Sub accounts to/from master |
| ZBA flush | EOD | Subs to master, master to external sweep |
| Notional pooling | None physical | Calculate net interest, no movement |

## Engine logic

```python
def evaluate_sweep(account):
    pos = current_position(account)
    target = account.target
    band = account.band
    if pos > target + band:
        excess = pos - target
        execute_outbound(account, excess)
    elif pos < target - band:
        shortfall = target - pos
        execute_inbound(account, shortfall)
```

## Multi-currency sweep

- Per-currency sweep within currency
- Cross-currency sweep = FX trade — separate decision (cost > benefit unless rate is right)

## Tax / legal layer

- Inter-entity transfers = potentially intercompany loans
- Transfer pricing — interest at arm's length
- Permanent establishment risks
- Notional pooling banned in some jurisdictions (US)
- Legal opinion per structure

## Tech components

- Sweep engine (rules, schedule)
- Position keeper (per account, per CCY)
- Booking engine (creates intercompany entries)
- Audit + tax reporting

## Linked

[[intraday-liquidity]] · [[../concepts/sweep]] · [[../concepts/zba]] · [[../architecture/in-house-bank-pattern]]
