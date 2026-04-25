# Letter of Credit (LC / Documentary Credit)

Bank guarantee of payment to seller upon presentation of compliant documents. Foundational trade finance instrument.

## Mechanics

```
Buyer ──> Issuing Bank ──> Advising Bank ──> Seller
                                  │
                                  └─> Confirming Bank (optional, takes risk)
```

1. Buyer applies for LC at issuing bank
2. Issuing bank issues LC, sends via SWIFT to advising bank in seller's country
3. Advising bank notifies seller
4. Seller ships goods, presents documents (BL, invoice, certs) to advising bank
5. Documents flow to issuing bank
6. Issuing bank checks vs LC terms; pays if compliant
7. Buyer reimburses issuing bank

## Common types

- **Sight LC** — payment on presentation of compliant docs
- **Usance / Deferred LC** — payment at maturity (e.g., 90 days)
- **Confirmed LC** — confirming bank adds independent payment guarantee
- **Standby LC (SBLC)** — see [[standby-lc]] — guarantee-like instrument
- **Transferable LC** — primary beneficiary can transfer to second beneficiary
- **Revolving LC** — auto-replenishes for ongoing trade

## Governing rules

- [[ucp-600]] — UCP 600 (Uniform Customs and Practice for Documentary Credits)
- ISBP 745 (International Standard Banking Practice for documentary examination)
- eUCP for electronic presentation

## SWIFT message types (legacy + ISO migration)

- MT700 — issuance
- MT701 — issuance continuation
- MT707 — amendment
- MT710 — advice through advising bank
- MT734/740/742 — refusal / advice of payment / reimbursement claim
- MT799 — free format follow-up

## Cash mgmt link

- Issuance backed by cash collateral or credit line
- Buyer's collateral / facility usage tracked
- Settlement at maturity = cash leg
- Drives intraday liquidity (issuance fees + reimbursement timing)

## Related

[[bank-guarantee]] · [[documentary-collection]] · [[standby-lc]] · [[ucp-600]] · [[../regulations/wtr-travel-rule]]
