# Intraday credit pricing

What banks charge for advancing funds during the day to bridge timing mismatches. Distinct from overnight lending.

## Sources of intraday credit

| Source | Rate basis | When used |
|---|---|---|
| Central-bank intraday | Free (most CBs) or marginal lending rate × intraday fraction | RTGS funding gap (T2, CHAPS, SIC) |
| Repo (bilateral or CCP) | Repo rate × hours/24 (rough) | Securities-cash leg, treasury |
| Lombard / collateralised credit line | Bank's published Lombard rate | SNB's standing facility |
| Uncollateralised intraday line | Annualised rate × hours, often free up to limit | Customer working capital, large corp |
| Emergency liquidity assistance (ELA) | Penalty: policy rate + 100–200 bps | Last-resort, very rarely |

## Free intraday — the default

- ECB (T2): Banks get free intraday liquidity against collateral; failure to repay by EOD becomes overnight marginal-lending advance (penalty rate).
- BoE (CHAPS): Same model — free intraday repo, EOD becomes Sterling Monetary Framework overnight rate.
- SNB (SIC): Free intraday repo against collateral.
- Fed (Fedwire): Has been a daylight overdraft fee model historically (charges per "peak overdraft × time"), now usage-based pricing.

Rationale: charging for intraday liquidity would push banks to hoard, degrading payment-system smoothness.

## When intraday becomes overnight

If counterparty fails to repay by EOD cut-off:
- Advance flips to overnight marginal lending rate (typically policy rate + 25–100 bps)
- Triggers regulatory reporting + counterparty risk treatment
- Repeat occurrences flag supervisory attention

## Pricing intraday for corporate clients

Banks usually offer:
- Free intraday line up to negotiated limit — embedded in [[../06-pricing-revenue]] account-analysis package
- Above-limit charged annualised rate × actual hours, rounded up to day
- Excess events: hard-stop OR proceed with penalty (relationship-driven)

## Sweep / liquidity products

Intraday liquidity products often bundle:
- Real-time positioning ([[../processes/intraday-liquidity]])
- Auto-funding from concentration account
- Interest credit on idle intraday positions (rare; mostly notional)

## Related

[[../processes/intraday-liquidity]] · [[repo]] · [[../operators/snb]] · [[../operators/ecb]] · [[../regulations/basel-iii]]
