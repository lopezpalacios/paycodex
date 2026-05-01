# Account tier

Balance band that determines applicable rate. Function of [[deposit-pricing]] segmentation.

## Marginal vs blended

**Marginal-tier** (industry standard):

```
Balance $5M, tiers: 0–$1M @ 2%, $1M–$10M @ 3%, $10M+ @ 3.5%
Tier 1 yield: $1M × 2% = $20,000
Tier 2 yield: $4M × 3% = $120,000
Total: $140,000 → blended yield 2.8%
```

**Blended-tier** (rarer, more generous):

```
Same $5M, balance "reaches" tier 2 → entire $5M @ 3% = $150,000
```

Marginal is what virtually every commercial bank uses today. If product docs say "X% on balances above Y", that's marginal.

## Setting tier thresholds

Typical drivers:
- Operational cost recovery — small-balance accounts amortise high fixed cost; tier 1 priced low
- Mass / mass-affluent / private-bank thresholds — €/$ 100k, 1m, 10m natural breaks
- LCR classification — separate band where deposit becomes "operational"
- Competitive moat — match major competitor's published tiers

## Re-tiering frequency

- Daily — for products that pay top-tier rate at any moment exceeding threshold
- Monthly average — mass standard; ADB determines tier
- Volume-based (rolling 90d) — relationship products that reward consistency

## Impact on customer behaviour

Tier thresholds drive:
- [[zba]] / [[sweep]] design — concentrate to reach top tier on master account
- [[notional-pooling]] (where legal) — sum balances notionally to qualify
- "Tier shopping" — customer fragments balances if anti-tier optimisation works in another product

## On-chain implementation

See [[../../paycodex-onchain/code/XX-tiered-rate-deposit.sol]] (tokenised deposit with tier struct in storage).

## Related

[[deposit-pricing]] · [[interest-calculation]] · [[zba]] · [[sweep]]
