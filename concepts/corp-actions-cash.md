# Corporate actions — cash impact

Cash flows triggered by corporate actions on held securities.

## Common cash events

| Event | Cash flow | Timing |
|---|---|---|
| Coupon (interest) | Inflow | Per coupon schedule |
| Dividend | Inflow | Per declared schedule |
| Redemption (maturity) | Inflow (principal + final coupon) | Maturity date |
| Subscription / rights issue | Outflow | Subscription window |
| Tender offer | Outflow / inflow | Per offer terms |
| Tax withholding | Reduction (gross to net) | At source |

## Process

1. Issuer announces (CA notification)
2. CSD propagates to holders via custody chain
3. Holder elects (where optional)
4. Settlement on payment date
5. Cash credited to nominee → custodian → underlying holder

## Cash mgmt integration

- Forecast: known coupon + dividend schedule months ahead
- Reconciliation: incoming corp-action cash matched to expected against position
- Tax: withholding rate determination + reclaim where applicable (DTT — double taxation treaty)
- AR-equivalent process for institutional holders

## Tech / data

- ISO 20022 corp action messages: seev.031 (notification), seev.039 (instructions), seev.036 (movement preliminary)
- Vendor: SmartStream, Broadridge, Asset Servicing data from CSDs

## Related

[[t2s]] · [[../operators/euroclear]] · [[../operators/clearstream]] · [[../processes/intraday-liquidity]]
