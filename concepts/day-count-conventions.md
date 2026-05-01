# Day-count conventions

How "time" in `interest = principal × rate × time` is measured. Picking the wrong one = wrong interest.

## The four conventions you need

| Code | Numerator | Denominator | Used for |
|---|---|---|---|
| **act/360** | Actual calendar days | 360 | EUR/USD money market, most short-tenor wholesale |
| **act/365 (fixed)** | Actual calendar days | 365 | GBP money market, CHF, most retail |
| **30/360** | Months × 30 + day diff | 360 | US bond market (legacy); some loan products |
| **act/act-ISDA** | Actual / actual (split by year) | 365 or 366 in leap | Sovereign bonds, ISDA swaps |

## Worked example — 90 calendar days, 3.50%, 1,000,000 principal

```
act/360:     1,000,000 × 0.0350 × 90/360 = 8,750
act/365:     1,000,000 × 0.0350 × 90/365 = 8,630
30/360:      1,000,000 × 0.0350 × 90/360 = 8,750  (same numerator if 30-day months)
act/act-ISDA: 1,000,000 × 0.0350 × 90/365 = 8,630  (no leap year span)
```

act/360 yields ~1.4% MORE interest than act/365 on the same headline rate — the rate is the same but the year is "shorter" so each day is fractionally bigger. Banks prefer act/360 for deposits they pay out (lower) and act/365 when receiving (higher) — actually inverse: act/360 makes a year "longer" in days, so each-day's slice yields more interest. Lender-friendly conventions get the bigger fraction.

## 30/360 sub-variants

- **30/360 (Bond/SIA)** — adjust EOM dates, US convention
- **30E/360 (Eurobond)** — treat day-31 as day-30
- **30E/360 ISDA** — variant for ISDA swaps with EOM rule

## Where which is used (CH/EU/UK)

| Currency / market | Convention |
|---|---|
| EUR money market (€STR, EURIBOR) | act/360 |
| GBP money market (SONIA) | act/365 |
| CHF money market (SARON) | act/360 |
| USD money market (SOFR) | act/360 |
| EUR bonds | act/act-ISDA |
| GBP gilts | act/act-ISDA |
| Swiss CHF bonds | 30/360 (some) or act/act |
| ISDA swaps | act/act-ISDA |

## Implementation

Always store as enum + helper, not string. Errors here = audit findings + revenue loss / overpayment.

```python
def days_and_denom(basis, from_dt, to_dt):
    days = (to_dt - from_dt).days
    if basis in ("act/360", "30/360"): return days, 360
    if basis == "act/365": return days, 365
    if basis == "act/act-isda": ...  # split by year
```

## Related

[[interest-calculation]] · [[reference-rates]] · [[../../paycodex-onchain/concepts/day-count-onchain]]
