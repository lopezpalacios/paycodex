# FTP — Funds Transfer Pricing

Internal pricing curve banks use to allocate funding between deposit-gathering and asset-generating units.

## What it does

Treasury "buys" deposits from branch / RM at FTP rate. Treasury "sells" funding to lending desk at FTP rate. Difference between FTP and customer-facing rates = unit's spread (margin).

```
RM acquires deposit @ 1.50%
Treasury credits RM @ FTP for that tenor (e.g. 3.20%)
Branch/RM margin: 3.20 − 1.50 = 170 bps
Treasury then funds loan, charges loan desk @ FTP + cost
Loan desk lends @ FTP + spread → loan desk margin
```

This decouples balance-sheet decisions: each unit optimises locally without internal cross-subsidy or P&L distortion.

## Building the FTP curve

Inputs:
- Risk-free rate ([[reference-rates]]) per tenor — base curve
- Liquidity premium — what bank pays to issue debt at that tenor
- Behavioural maturity — for non-maturity deposits, modelled duration not contractual
- Term structure — bonds, swaps, CD market

Output: term-structured FTP rates that match-fund the asset side. A 5-year fixed-rate mortgage gets matched to 5-year-modelled-duration deposit funding, priced at 5-year FTP.

## Why behavioural maturity matters

Demand deposits are contractually overnight. But empirically they sit for 3–7 years on average (sticky). FTP gives them credit for that empirical duration → branch earns the spread between long-end FTP and overnight deposit rate. This is where deposit franchises produce earnings.

If rate shock + run risk causes betas to spike, behavioural maturity collapses → FTP spread vanishes → SVB-type compression.

## Two regimes

- **Single-curve FTP** — same curve for assets + liabilities. Simple, but ignores funding-gap costs.
- **Dual-curve / Liquidity Transfer Pricing** — separate liquidity premium charged to assets that consume liquidity. Industry standard post-2010.

## Linkage to deposit pricing

[[deposit-pricing]] derives "rate I can pay customer" from "FTP credit I get from treasury". If treasury cuts FTP credit (rate-cut environment), branch must cut deposit rate to maintain margin → deposit beta < 1.

## Related

[[deposit-pricing]] · [[interest-calculation]] · [[interest-rate-risk]] · [[../05-relationships]]
