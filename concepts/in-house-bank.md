# In-house bank

Central treasury entity acting as internal bank for corporate group.

## Functions

- Intercompany payments + netting
- POBO / ROBO (Payments / Receipts On Behalf Of)
- Group FX hedging
- Investment + funding management
- Cross-entity liquidity pooling

## Why corps build it

- Reduce external bank fees (intercompany flows internalized)
- Better FX position management at group level
- Control + visibility of group cash
- Tax optimization (where legally permitted)

## Tech

- TMS-anchored (Kyriba, GTreasury, FIS, ION)
- Multi-currency multi-entity ledger
- Integration with all subsidiary ERPs

## Tax / regulatory

- Intercompany loans — transfer pricing rules apply
- Permanent establishment risk if IHB acts cross-border
- Some jurisdictions restrict POBO (e.g., Brazil, China)

## Related

[[payment-factory]] · [[../architecture/in-house-bank-pattern]] · [[../processes/intraday-liquidity]]
