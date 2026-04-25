# Documentary Collection (D/C)

Bank handles documents on behalf of seller, not bank-guaranteed. Cheaper than LC but carries more seller risk.

## Variants

- **D/P (Documents against Payment)** — buyer pays before getting docs (releases goods)
- **D/A (Documents against Acceptance)** — buyer accepts bill of exchange (bank lets docs go), pays at maturity

## Mechanics

```
Seller ──> Remitting Bank ──> Collecting Bank ──> Buyer
```

- Seller ships, gives docs to remitting bank
- Remitting bank sends docs + collection instruction to collecting bank in buyer's country
- Collecting bank presents docs to buyer
- D/P: buyer pays, gets docs
- D/A: buyer accepts draft, gets docs

## Vs LC

- No bank guarantee — banks act as agent only
- Cheaper than LC (no committed credit line)
- Higher seller risk (buyer can refuse to pay/accept)
- Used between trusted counterparties or with established trade history

## Governing rules

- URC 522 (Uniform Rules for Collections, ICC)

## SWIFT messages

- MT400 — advice of payment
- MT410 — acknowledgment
- MT416 — advice of non-payment / non-acceptance

## Related

[[letter-of-credit]] · [[bank-guarantee]]
