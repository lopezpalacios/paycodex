# CBPII — Card-Based Payment Instrument Issuer

PSD2 third-party type that issues payment cards linked to underlying bank account at another PSP.

## Concept

- TPP issues card branded under scheme (Visa/MC)
- Card transactions hit customer's account at original bank
- Bank queries CBPII (via PSD2 API): "is funds available?" before authorizing

## Status

- Underused vs AISP / PISP
- "Funds confirmation" call standardized in PSD2 RTS
- Some EMI use case

## Related

[[aisp]] · [[pisp]] · [[../concepts/card-schemes]] · [[../regulations/psd2-psd3]]
