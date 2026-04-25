# Wire / High-Value Payments (CH + EU + UK focus)

Real-time gross settlement (RTGS) for high-value, irrevocable payments. Different rail per currency.

## CHF — [[sic]]

- Operated by SIX on behalf of [[../operators/snb]]
- Single rail handles wholesale + retail (uncommon globally)
- ISO 20022 native

## EUR — [[t2]]

- Eurosystem RTGS (replaced TARGET2 March 2023)
- Cutoff 18:00 CET
- Direct + indirect (correspondent) participation
- Most CH banks reach EUR via [[eurosic]] or correspondent

## GBP — [[chaps]]

- Bank of England operated
- Cutoff 18:00 GMT
- Property + wholesale dominant use
- ISO 20022 migrated 2023

## Cross-border — [[swift]]

- Messaging layer (FIN / pacs.008 under MX)
- Settlement via correspondent chain or CLS for FX
- gpi adds end-to-end tracking with UETR
- Subject to [[../regulations/wtr-travel-rule]]

## Properties (all rails)

- Final and irrevocable on settlement
- Credit-push only
- High fees vs batch / instant
- Manual repair common on bad beneficiary data

## Fraud

Top BEC vector. Callback verification mandatory in [[../07-risk-controls]]. [[vop]] / [[cop]] mitigate at point of initiation.

## Related

[[sic]] · [[t2]] · [[chaps]] · [[swift]] · [[iso-20022]] · [[../concepts/legacy-us/fedwire-chips]]
