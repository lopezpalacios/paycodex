# Reference rates

Indices that float-rate products reference. Set by central banks or scheme operators; published daily; audited by regulators.

## The post-LIBOR landscape (2024+)

LIBOR officially dead 2023. Replaced by overnight risk-free rates (RFRs):

| Currency | Old (LIBOR) | New RFR | Administrator | Day-count |
|---|---|---|---|---|
| USD | USD LIBOR | **SOFR** Secured Overnight Financing Rate | NY Fed | act/360 |
| EUR | EURIBOR (still alive but reformed) + EONIA (dead) | **€STR** Euro Short-Term Rate | ECB | act/360 |
| GBP | GBP LIBOR | **SONIA** Sterling Overnight Index Average | BoE | act/365 |
| CHF | CHF LIBOR | **SARON** Swiss Average Rate Overnight | SIX | act/360 |
| JPY | JPY LIBOR | TONAR | BoJ | act/365 |

EURIBOR survived as the EU term-lending benchmark for legacy reasons but is reformed (hybrid methodology, BMR-compliant).

## Critical structural difference: RFRs are backward-looking

LIBOR was forward-looking term rates (1m, 3m, 6m). RFRs are overnight, compounded in arrears for term equivalents. This means:

- A 3-month SOFR-linked loan rate is NOT known until the period ends (compounding-in-arrears)
- Lookback or shift conventions used to make rates payable on time
- Term SOFR (forward) exists but constrained to certain product types (CME-administered)

Banks have rebuilt mortgage, syndicated loan, and floating-rate note product lines around this.

## Reset frequency

- **Daily reset** — overnight RFRs, most floating-rate notes
- **Periodic reset** — term-rate products: 1m/3m/6m EURIBOR, term SOFR
- **Continuous accrual** — DLT/onchain instruments may compute per-block

## Spread

`effective rate = reference + spread`. Spread is set at origination, fixed for life of instrument (typically). Spread reflects credit, liquidity, term premium.

For deposit products: bank pays `reference - spread` (deposit beta < 1 — see [[deposit-pricing]]).

## In on-chain instruments

References pulled via oracle. See [[../../paycodex-onchain/concepts/oracle-rate-feeds]]. Trust model: oracle source, signing, fallback. €STR/SOFR being public + central-bank-published makes oracle attestation cleaner than market-derived rates.

## Known issues

- **Stale data over weekends/holidays** — last value carried forward; some products use weighted-day adjustment
- **Index cessation events** — if RFR administrator stops, fallback to triggered backup (BMR Article 28b)
- **Tax treatment of synthetic vs natural compounding** — varies by jurisdiction

## Related

[[interest-calculation]] · [[day-count-conventions]] · [[deposit-pricing]] · [[negative-interest]] · [[../../paycodex-onchain/concepts/oracle-rate-feeds]]
