# ZBA — Zero Balance Account

Subsidiary DDA that holds no overnight balance. Sweeps to master at EOD, funded back morning to cover debits.

## Mechanics

- Master account = concentration point
- ZBA subs = payroll, AP, branch accounts
- Bank auto-moves cash to net the sub to \$0 each day
- Funding back is just-in-time when debits hit

## Why corps use it

- One pool earns interest / [[ecr]] instead of fragmented balances
- Tighter fraud control — sub accounts can't be drained beyond same-day funding
- Visibility — every entity has its own account but treasury controls cash centrally

## Why banks like it

- Sticky operating deposits (high LCR value, see [[06-pricing-revenue]])
- Multiple accounts = more fees per [[account-analysis]]

## Related

[[sweep]] · [[02-products]] · [[06-pricing-revenue]]
