# NSFR — Net Stable Funding Ratio

Basel III long-term liquidity ratio. Stable funding ≥ required stable funding over 1 year.

## Formula

```
NSFR = Available Stable Funding / Required Stable Funding
NSFR ≥ 100% required
```

## ASF (Available Stable Funding) factors

- Capital + long-term liabilities: 100%
- Stable retail deposits: 95%
- Less stable retail: 90%
- Operating wholesale deposits (corps, financials): 50%
- Non-operating wholesale: 0% (cliff effect)

## RSF (Required Stable Funding) factors

- HQLA Level 1: 5%
- HQLA Level 2A: 15%
- Loans to financials >1y: 100%
- Mortgages: 65-85%

## Why cash mgmt cares

- Same operating-deposit story as LCR
- Term deposits (1y+) get full ASF credit → bank pays more for term
- Drives product design + pricing

## Related

[[lcr]] · [[../regulations/basel-iii]] · [[../06-pricing-revenue]]
