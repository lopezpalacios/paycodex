# 06 — Pricing & Revenue (CH + EU + UK)

How bank charges, how bank earns.

## Account analysis statement

Monthly billing artifact. Detail: [[concepts/account-analysis]].

- AFP service codes (US-origin but adopted globally)
- Each service: volume × unit price = gross fee
- Average ledger balance × [[concepts/ecr]] × (1 - reserve req) = earnings credit
- Net fee = gross fee - earnings credit, billed if positive

## SEPA pricing rules

- Reg 924/2009 + 260/2012: cross-border EUR SEPA payment must cost same as domestic
- IPR ([[regulations/instant-payments-regulation]]): [[concepts/sct-inst]] cannot exceed [[concepts/sepa-sct]] price
- These constrain pricing power on EUR rails

## Hard-dollar fees (typical EU/CH/UK ranges)

- Per [[concepts/sepa-sct]]: €0.05-0.30
- Per [[concepts/sct-inst]]: now capped at SCT-equivalent under IPR
- Per [[concepts/sepa-sdd]]: €0.10-0.50 (creditor side)
- Per [[concepts/sic]] payment: CHF 0.05-0.20
- Per [[concepts/wire]] (T2/CHAPS/SIC RTGS): €/CHF/£ 5-25
- [[concepts/lockbox]]: declining
- Volume discounts, tiered pricing

## Bank revenue stack

1. Fees (hard dollar) — [[concepts/account-analysis]]
2. Net interest margin on deposits — see [[concepts/deposit-pricing]] · [[concepts/ftp]] · [[concepts/interest-rate-risk]]; especially CHF deposits at SNB after [[concepts/negative-interest]] exit
3. Float on payments-in-transit (compressed by instant rails)
4. FX spread (10-50 bps retail, 1-5 bps wholesale)
5. Interchange on commercial cards
6. Cross-sell to lending / IB ([[05-relationships]] RM owns)

## Interest-bearing products — calculation chain

Customer rate ← [[concepts/deposit-pricing]] ← FTP curve ← policy rate + bank's [[concepts/interest-rate-risk]] hedging cost.

For posted interest: see [[concepts/interest-calculation]] · [[concepts/day-count-conventions]] · [[processes/interest-posting]] · [[concepts/withholding-tax]].

For floating products: [[concepts/reference-rates]] (€STR, SOFR, SARON, SONIA, post-LIBOR).

For tiered products: [[concepts/account-tier]].

For programmable / on-chain analogues: [[../paycodex-onchain/concepts/interest-accrual-onchain]] and the runnable PoC at `paycodex-rules-poc/`.

## Deposit value (post-2023)

- Operating deposits = sticky, low beta = high LCR value (Basel III)
- Bank willing to lose money on fees to win deposits
- Non-operating deposits penalized post-SVB / Credit Suisse turbulence
- Drives bank product design — [[concepts/zba]], [[concepts/sweep]] all keep balances onshore

## Cross-links

Volumes from [[04-daily-ops]]. Negotiated in [[01-onboarding]] RFP. RM owns total P&L ([[05-relationships]]).

← [[README]]
