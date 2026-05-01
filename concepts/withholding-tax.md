# Withholding tax (interest)

Tax deducted at source on interest paid. Bank withholds, remits to tax authority, customer claims credit on annual return (or treaty relief).

## CH — Verrechnungssteuer (VST)

- **Rate:** 35% on interest ≥ CHF 200/yr (per account, per bank)
- **Authority:** ESTV (Eidgenössische Steuerverwaltung)
- **Reclaim:** Swiss residents reclaim on annual tax return; non-residents via DTA (treaty)
- **Scope:** Interest on Swiss bank deposits, Swiss bonds. NOT on foreign-source interest.
- **Trigger:** Posting event. Accrual ≠ taxable; capitalisation = taxable.

Example: 1,500,000 CHF deposit @ 1.5% simple act/365 for 1 year = 22,500 CHF gross. WHT = 7,875. Net credited = 14,625.

## EU — DAC2 / CRS reporting (no withholding)

EU abandoned EUSD savings withholding 2017. Replaced by DAC2 / CRS (automatic exchange of information). No tax deducted at source; bank reports interest to home tax authority. Customer pays at marginal rate on personal return.

Exception: some member states retained domestic-source WHT (e.g. Germany Abgeltungsteuer 25% on bank interest for residents).

## UK — Gross interest since 2016

PSA (Personal Savings Allowance) since 6 April 2016: banks pay interest GROSS, customer pays via self-assessment if above PSA (£1,000 basic-rate, £500 higher-rate, £0 additional-rate).

Pre-2016: 20% basic-rate WHT was standard.

## Cross-border with treaty relief

When non-resident depositor opens account, source-country WHT applies UNLESS double-tax treaty reduces. Common reductions to 0%, 5%, 10%, or 15%.

Process:
1. Customer provides residency certificate + treaty form (CH: 80, 81, 82 series; EU: domestic equivalents)
2. Bank applies treaty rate at posting
3. Customer claims relief in residence country

Compliance burden — some banks decline to apply treaty rates and require post-hoc reclaim.

## Operational checklist for the bank

| Step | System |
|---|---|
| Identify customer tax residence | [[../01-onboarding]] KYC + tax residency cert |
| Determine product taxability | Product master (interest-bearing flag, exemption flags) |
| Compute WHT at posting | Interest engine + tax engine |
| Remit to authority | Tax remittance schedule (CH: quarterly, varies elsewhere) |
| Issue tax voucher to customer | Annual statement, e.g. CH form 1135 |
| Report to tax authority | Annual filing |

## On-chain treatment

For tokenised deposits, WHT becomes a smart-contract concern:
- `withholding.enabled` flag in rule schema
- `postInterest()` deducts WHT amount, transfers to tax-collection address
- Audit trail = on-chain event log (advantage over off-chain bookkeeping)

See `InterestBearingDeposit.sol` and example rule `08-ch-withholding.json`.

## Related

[[interest-calculation]] · [[../processes/interest-posting]] · [[../regulations/eu-dac2]] · [[../regulations/swiss-amla]]
