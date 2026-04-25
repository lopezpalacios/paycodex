# FX Options

Right (not obligation) to exchange currencies at agreed rate on / before agreed date.

## Variants

- **Vanilla** — call / put on currency pair
- **Barrier** — knock-in / knock-out at threshold
- **Asian** — payoff based on average rate
- **Digital** — fixed payoff if condition met
- **Forward extra** — forward + option combination

## Use

- Hedge tail risk while keeping upside
- Premium-financed strategies (zero-cost collars)
- Speculative

## Pricing

- Black-Scholes / Garman-Kohlhagen for vanilla
- Implied vol surface for non-vanilla
- Greeks: delta, gamma, vega, theta, rho

## Hedge accounting

- More complex than forwards under IFRS 9
- Often split into intrinsic + time value (IFRS 9 allows time-value cost-of-hedging)

## Reg

- Cleared via CCP per [[../regulations/emir]] for some standard types
- Margin requirements for non-cleared

## Related

[[fx-forward]] · [[hedge-accounting]] · [[../regulations/emir]]
