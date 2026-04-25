# T2S — TARGET2-Securities

Eurosystem securities settlement platform. Delivery-versus-payment in central bank money for EUR (and other connected currencies via CCB models).

## Properties

- Operated by ECB (technical: 4CB consortium — DE, ES, FR, IT central banks)
- DvP Model 1 (gross-gross)
- Settles ~700K instructions / day across multiple CSDs
- Connected CSDs: 21+ (Euroclear ESES, Clearstream, Iberclear, Monte Titoli, etc.)
- Multi-currency: EUR primary; DKK live; non-EUR via CCB (Currency Central Bank) model

## Architecture concept

```
CSDs ──> T2S ──> ECB / NCB cash accounts (DCAs)
                  │
                  └─> T2 (RTGS) liquidity transfers
```

## DCA — Dedicated Cash Account

- Bank's T2S settlement account at NCB
- Funded from main T2 account
- Auto-collateralization: pre-pledged securities convert to credit in DCA when needed

## Use for cash mgmt

- Treasury repo settlement (tri-party via [[../operators/euroclear]] / [[../operators/clearstream]])
- Bond + equity settlement cash legs
- Drives intraday liquidity demand
- DCA position management = critical intraday operation

## Related

[[t2]] · [[dvp]] · [[../operators/ecb-eurosystem]] · [[../operators/euroclear]] · [[../operators/clearstream]]
