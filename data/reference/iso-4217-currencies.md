# ISO 4217 currencies

Currency code list. Subset relevant for CH/EU/UK cash mgmt.

| Code | Name | Minor units |
|---|---|---|
| EUR | Euro | 2 |
| CHF | Swiss franc | 2 |
| GBP | Pound sterling | 2 |
| USD | US dollar | 2 |
| JPY | Yen | 0 |
| SEK | Swedish krona | 2 |
| NOK | Norwegian krone | 2 |
| DKK | Danish krone | 2 |
| PLN | Polish zloty | 2 |
| CZK | Czech koruna | 2 |
| HUF | Hungarian forint | 2 |
| RON | Romanian leu | 2 |
| BGN | Bulgarian lev | 2 |
| HRK | (retired 2023, replaced by EUR) | — |
| AUD | Australian dollar | 2 |
| CAD | Canadian dollar | 2 |
| CNY | Renminbi | 2 |
| HKD | Hong Kong dollar | 2 |
| SGD | Singapore dollar | 2 |

Full list: ISO 4217 published by SIX (Swiss interesting trivia: SIX is registration authority for ISO 4217).

## Validation

- Code must exist + be active on payment date (not retired)
- Minor units determine decimal precision in amount field
- Some pairs forbidden by sanctions (e.g., RUB to certain accounts post-2022)

## Linked

[[../payment-entity]]
