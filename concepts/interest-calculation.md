# Interest calculation

Translation of an interest-rate policy into a cash amount. Sits between [[deposit-pricing]] (rate setting) and [[../processes/interest-posting]] (booking).

## Anatomy of an interest amount

```
interest = principal × rate × time × (1 - withholding)
```

But each term has structure:

| Term | Components |
|---|---|
| **principal** | Avg daily balance, point-in-time, or weighted (per posting frequency) |
| **rate** | Fixed | reference + spread | tiered | KPI-adjusted | floored/capped |
| **time** | Days × day-count basis ([[day-count-conventions]]) |
| **withholding** | Tax regime, residency, treaty relief ([[withholding-tax]]) |

## Two formula families

### Simple

```
interest = principal × (rateBps / 10000) × (days / denom)
```

Used for: most demand deposits, money-market instruments, short-tenor loans.

### Compound

```
interest = principal × ((1 + r/n)^n×t - 1)
```

`n` = compounding frequency (daily=365 or 360, monthly=12, continuous→exp(rt)). Used for: retail savings, structured deposits, longer-tenor instruments.

For continuous compounding: `interest = principal × (e^(r×t) - 1)`.

## Accrual basis vs cash basis

- **Accrual basis** — interest earned daily, recognised in P&L as it accrues, even if not yet posted to customer. GL entry: Dr Interest expense / Cr Interest payable.
- **Cash basis** — interest only recognised when posted (taxable event). Sub-bookkeeping needed for accrual-vs-posted reconciliation.

Banks book accrual; customer-facing posting is at frequency defined by product T&Cs.

## Posting frequency

- Daily — money-market and wholesale instruments
- Monthly — most demand and savings accounts
- Quarterly — retail savings, sometimes paired with [[withholding-tax]] events
- At maturity — term deposits, fixed-term loans
- At redemption — tokenised products ([[../../paycodex-onchain/concepts/interest-accrual-onchain]])

Posting capitalises accrued interest into principal. For loans, customer pays it. For deposits, bank pays it (or credits the account).

## Average vs point-in-time balance

- **Avg daily balance (ADB)** — sum of EOD balances ÷ days. Standard for most deposit interest.
- **Avg collected balance** — ADB minus float adjustments. Used for [[ecr]] in US-style commercial.
- **Point-in-time** — balance at posting moment. Crude; only used for instruments with stable principal.
- **Weighted-by-event** — for accounts with frequent volatility, integrate over time.

The choice affects how much interest a corp earns when balance is volatile — material difference for treasury operations.

## Edge cases

- **Leap year** — act/365 still uses 365 in denom; act/act-isda uses 366 in leap years.
- **Weekends / holidays** — day count is calendar-day (act) or business-day (variants); banks use calendar-day for deposits, business-day for some loan products.
- **Mid-period rate change** — split period: accrue old rate to change date, new rate from change date.
- **Negative rates** — see [[negative-interest]]; pass-through varies by product and customer segment.
- **Fee netting** — for [[ecr]] (two-track), interest may net against fees rather than pay cash.

## Sanity benchmark

| Tenor | Principal | Rate | Simple act/360 | Compound daily 365 |
|---|---|---|---|---|
| 30d | 1,000,000 | 3.50% | 2,917 | 2,879 |
| 90d | 1,000,000 | 3.50% | 8,750 | 8,694 |
| 360d | 1,000,000 | 3.50% | 35,000 | 35,617 |

Compound > simple for >1 year; less than simple short-tenor (because act/360 vs 365 in compound denom inflates simple).

## Related

[[day-count-conventions]] · [[reference-rates]] · [[deposit-pricing]] · [[withholding-tax]] · [[ecr]] · [[../processes/interest-posting]] · [[../06-pricing-revenue]] · [[../../paycodex-onchain/concepts/interest-accrual-onchain]]
