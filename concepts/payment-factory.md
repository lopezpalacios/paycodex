# Payment factory

Centralized payment processing entity for corporate group. Often inside [[in-house-bank]].

## Patterns

- **POBO** — payments on behalf of subsidiaries
- **ROBO** — receipts on behalf of subsidiaries
- **Hybrid** — POBO for AP, subs keep their own collection accounts

## Benefits

- Reduced bank account count
- Consolidated banking spend
- Standardized payment file processing
- Single connection per bank

## Tech

- Multi-source ERP ingest
- Canonical normalization (ISO 20022)
- Routing engine (rail + bank selection)
- Multi-bank gateway

## Related

[[in-house-bank]] · [[../architecture/payment-factory-pattern]] · [[../concepts/tms]]
