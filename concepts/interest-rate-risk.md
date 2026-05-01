# Interest rate risk (IRRBB)

The risk that interest-rate movements impair earnings or capital. Regulated under Basel III IRRBB framework.

## Two complementary metrics

### NII sensitivity (earnings perspective)

```
ΔNII = projected interest income/expense change under rate shock, over fixed horizon (1 yr usually)
```

- Captures short-term P&L volatility
- Bank wants stable NIM despite rate moves
- Triggered by repricing-mismatch — assets vs liabilities reprice on different tenors

### EVE sensitivity (economic-value perspective)

```
ΔEVE = change in present value of all future cash flows under rate shock
```

- Captures balance-sheet vulnerability
- Driven by duration mismatch — long-tenor fixed-rate assets funded by short-tenor deposits
- Regulator-imposed cap: ΔEVE under prescribed shocks ≤ 15% of Tier 1 capital (EU IRRBB)

## Rate shock scenarios (regulator-prescribed)

EBA / BCBS standard shocks:
1. Parallel shock up (+200 bps)
2. Parallel shock down (−200 bps, floored at zero)
3. Steepener (short rates down, long up)
4. Flattener (short up, long down)
5. Short-rate shock up
6. Short-rate shock down

Bank computes ΔNII and ΔEVE under each, reports worst-case to supervisor. EU thresholds: ΔEVE ≤ 15% Tier 1 ≤ "outlier test" trigger.

## Behavioural assumptions — the fudge factors

Most contentious inputs:

| Assumption | Why it matters |
|---|---|
| **Deposit beta** ([[deposit-pricing]]) | If betas are 0.3, balance sheet looks safer than if 0.8 |
| **Deposit duration** | Modelled life of "non-maturity deposits" — common 3–7 yr; longer = more rate-locked |
| **Prepayment** | Mortgage prepayment under rate-down scenario reshapes asset duration |
| **Credit-line drawdown** | Off-balance commitments turn into rate-sensitive assets |

Supervisors challenge banks aggressively on these. SVB (2023) failed in part because deposit-duration assumptions ignored that uninsured deposits ARE rate-sensitive and beta=1 in stress.

## Hedging instruments

- IRS (interest-rate swaps) — pay fixed/receive floating to convert long fixed-rate assets to floating
- Caps / floors — protect against tail moves
- FRAs / futures — short-tenor hedge
- Cross-currency basis — for multicurrency books

Hedge accounting ([[hedge-accounting]]) determines whether hedge effectiveness flows through P&L or OCI.

## Linkage to deposit pricing

[[deposit-pricing]] and IRRBB are tightly coupled. If treasury overestimates deposit beta → understates interest-rate risk → undercharges loans → margin compression when rates move. SVB-style.

## Related

[[interest-calculation]] · [[deposit-pricing]] · [[reference-rates]] · [[hedge-accounting]] · [[../regulations/basel-iii]] · [[../nfr/]]
