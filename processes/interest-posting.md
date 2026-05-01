# Interest posting — L3

Daily accrual + periodic capitalisation pipeline. Sits between rate-setting ([[../concepts/deposit-pricing]]) and customer statement.

## Daily process (EOD)

```python
for account in active_interest_bearing_accounts:
    balance = compute_balance(account, today)         # ADB or point-in-time per product T&Cs
    rate    = get_effective_rate(account, today)      # fixed | floating | tiered | KPI
    days    = 1                                       # one-day accrual
    denom   = day_count_denom(account.basis)
    accrued = balance * rate_bps * days / (10000 * denom)
    
    book(
        Dr "Interest Expense" (P&L),
        Cr "Accrued Interest Payable" (B/S, customer-side liability)
    )
    update_accrual_subledger(account, accrued)
```

Daily accrual is mechanical. Quality issues: rate change mid-day, balance volatility, holiday handling.

## Posting (capitalisation)

At posting frequency (monthly/quarterly/at-maturity):

```python
gross = accrual_subledger.get_total(account, period)
wht   = compute_wht(gross, account.tax_residence, account.product)  # see [[../concepts/withholding-tax]]
net   = gross - wht

book(
    Dr "Accrued Interest Payable",
    Cr "Customer Account" (net),
    Cr "WHT Payable to Authority" (wht),
)
issue_statement(account, gross, wht, net)
```

## Edge cases

| Case | Handling |
|---|---|
| Rate change mid-period | Split: pre-change at old rate, post-change at new |
| Balance change mid-day | Use ADB or weighted balance (per product) |
| Account close mid-period | Pro-rata accrual to close date, post immediately |
| Negative interest pass-through | If product allows: customer DEBIT instead of credit; usually require explicit T&Cs |
| Withholding tax change | Apply rate effective at posting date, not accrual date |
| Tier crossing mid-period | Marginal-tier: each balance slice at applicable band; recompute daily |
| Leap year (Feb 29) | act/365 still uses 365 denom; act/act-isda uses 366 |

## Reconciliation

Daily accrual GL must reconcile to:
1. Sub-ledger sum across all interest-bearing accounts
2. Modelled NII forecast (variance investigated > X bps)
3. Bank-wide interest-expense P&L line
4. Customer statements at posting period end

## Tech components

- **Rate engine** — sources fixed/floating rates per account
- **Day-count library** — typed enum, not strings
- **Accrual sub-ledger** — per-account, per-day accrual records
- **Posting orchestrator** — schedules monthly/quarterly runs
- **Tax engine** — withholding computation + remittance
- **Statement generator** — customer-facing artifact

## On-chain analogue

Smart-contract version: `_accrueToNow()` on every state-change updates accrued amount; `postInterest()` capitalises and applies WHT in one tx. See [[../../paycodex-rules-poc]] `InterestBearingDeposit.sol`.

Advantage: the ON-chain accrual sub-ledger IS the customer-side audit trail. Disadvantage: gas cost, finality timing.

## Related

[[../concepts/interest-calculation]] · [[../concepts/withholding-tax]] · [[../concepts/deposit-pricing]] · [[../concepts/account-tier]] · [[../04-daily-ops]] · [[../../paycodex-onchain/concepts/interest-accrual-onchain]]
