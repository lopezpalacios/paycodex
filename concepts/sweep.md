# Sweep

Auto-move balances to optimize yield or pay down debt.

## Types

- **Investment sweep** — excess to MMF, repo, Eurodollar deposit
- **Loan sweep** — pay down revolver instead of investing (cheaper than borrow rate > MMF yield)
- **Notional pooling** — no physical movement, bank nets balances for interest calc. Banned in US, common EU/Asia.
- **Target balancing** — keep account at \$X, sweep excess to master
- **Cross-currency sweep** — multicurrency notional pooling

## Mechanics

- Triggered EOD (some intraday)
- Bank acts as agent, moves funds per agreement
- Tax / legal entity considerations — intercompany loans flagged

## Related

[[zba]] · [[02-products]] · [[04-daily-ops]]
