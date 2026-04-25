# Card schemes (Visa, Mastercard, UnionPay, Amex, Diners, JCB)

Global / regional card networks. Define rules + clearing + settlement for cards bearing their brand.

## Major schemes

| Scheme | HQ | Coverage | Model |
|---|---|---|---|
| Visa | US | Global | 4-party |
| Mastercard | US | Global | 4-party |
| Amex | US | Global | 3-party (issuer + network) |
| UnionPay | CN | Global (CN-strong) | 4-party |
| JCB | JP | Global (JP-strong) | 4-party |
| Diners | US | Global | 3-party (Discover-owned) |
| Cartes Bancaires (CB) | FR | FR domestic + co-branded | 4-party |
| girocard | DE | DE domestic | 4-party |

## 4-party model

```
Cardholder ←→ Issuer (cardholder bank) ←→ Network ←→ Acquirer (merchant bank) ←→ Merchant
```

- Cardholder: holds card
- Issuer: issued the card (bears credit risk)
- Network: clearing + scheme rules
- Acquirer: provides merchant acceptance
- Merchant: accepts card

## Cash mgmt link

- Treasury manages **issuer-side** funding (settlement of cardholder transactions to merchants via networks)
- Treasury manages **acquirer-side** receipts (merchant settlement files, reserves, holdback)
- Commercial card programs (P-card, T&E, virtual card) sit on top — see [[commercial-card]]

## Settlement

- Daily net file from network → bank settlement account
- Multi-currency: settled in scheme settlement currency (USD primarily for international)
- Disputes (chargebacks) handled via network rules + scheme dispute portals

## Related

[[commercial-card]] · [[virtual-card]] · [[interchange]]
