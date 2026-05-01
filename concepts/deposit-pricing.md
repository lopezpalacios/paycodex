# Deposit pricing

How banks set the rate they pay on deposits. Output of ALM (asset-liability management) committee, executed by treasury / pricing desk.

## Core formula

```
deposit rate = reference rate × beta − operating cost − liquidity premium ± segment adjustment
```

- **Reference rate** — policy rate proxy (€STR, SARON, SONIA, SOFR)
- **Beta** — fraction of policy-rate move passed through. Operating deposit beta typically 0.2–0.5; non-op 0.7–0.9.
- **Operating cost** — transaction processing, statementing, ops overhead amortised across deposits
- **Liquidity premium** — discount for stable balances (LCR-favourable), penalty for run-prone balances
- **Segment adjustment** — relationship pricing, total-wallet view, RM discretion

Net result: bank deposit rate < policy rate; spread = NIM (net interest margin) contribution.

## Deposit beta — the most-watched input

Beta = (Δ deposit rate) / (Δ policy rate). Tracked per segment.

| Segment | Typical beta (rising rates) | Why |
|---|---|---|
| Retail demand | 0.10–0.25 | Sticky, low rate sensitivity, switching cost |
| Retail savings | 0.30–0.50 | Some price awareness |
| Corporate operating | 0.20–0.40 | Operational stickiness, RM moderation |
| Corporate non-op (incl HYSA) | 0.60–0.95 | Treasury aggressively shops |
| Wholesale (interbank) | ≈1.0 | Pure rate market |

Asymmetry: betas ON THE WAY UP often lag betas ON THE WAY DOWN — banks slow to raise, fast to cut. Subject to political/regulatory scrutiny (US FDIC, EU consumer protection).

## ALM and FTP linkage

Deposit pricing isn't free-form. Each deposit is funded into the balance sheet via [[ftp]] (funds transfer pricing):

```
branch / RM "buys" deposit funding from treasury at internal FTP curve
treasury "sells" same funding to lending desk
```

FTP curve based on policy rate + bank's liquidity profile. Branch/RM keeps spread between FTP and customer deposit rate. Margin = NIM contribution.

## Tiered pricing

Balance bands → different rates per band. See [[account-tier]]. Two flavours:

- **Marginal-tier** — each balance dollar accrues at the band it falls in (industry standard)
- **Blended-tier** — entire balance gets the rate of the highest band it reaches (rarer; higher payout)

Tier thresholds reflect:
- Operational cost amortisation (small balances cost more per $)
- Customer segmentation (mass-affluent thresholds)
- Liquidity value of large stable balances

## Liquidity-driven pricing (post-Basel III)

Basel III LCR (Liquidity Coverage Ratio) classifies deposits by run risk:

| LCR category | Run-off rate | Pricing implication |
|---|---|---|
| Operational, insured | 5% | Premium pricing, bank wants to keep |
| Operational, uninsured | 25% | Modest premium |
| Non-operational, insured | 5% | Premium |
| Non-operational, uninsured | 40% | Penalty pricing or refused |
| Non-operational, financial entity | 100% | Often refused entirely |

Post-SVB / Credit Suisse (2023): non-op deposit haircuts widened. Some banks now pay BELOW market on hot money, REFUSE financial-entity non-op deposits.

## ECR pricing alternative

In US/Caribbean, banks offer [[ecr]] (earnings credit rate) as a soft-dollar alternative. Same NIM economics for the bank, different ergonomics for the corp.

## Negative-rate environment overlay

When policy rate is negative, [[negative-interest]] mechanics kick in: tiered exemptions (Swiss SNB-style historically), pass-through to large deposits, NIM compression.

## Related

[[interest-calculation]] · [[reference-rates]] · [[ecr]] · [[ftp]] · [[account-tier]] · [[negative-interest]] · [[../06-pricing-revenue]] · [[../regulations/basel-iii]]
