# Receivables — QR-bill vs Virtual Accounts vs Lockbox vs eBill

| Aspect | [[../concepts/qr-bill]] | [[../concepts/virtual-accounts]] | [[../concepts/lockbox]] | [[../concepts/ebill]] |
|---|---|---|---|---|
| Geography | CH | Global (esp NL, DE, UK) | Mostly UK / paper-heavy industries | CH |
| Channel | Paper + PDF + scan | Any incoming credit | Paper cheque | Digital invoice |
| Reference | Structured (QRR / SCOR) | Virtual IBAN per customer | OCR / manual | Same as QR-bill |
| Auto-match rate | 90%+ for structured | Near 100% for known customer | 60-80% (declining) | 95%+ |
| Setup cost | Low (per invoice ref) | Per VA range / setup | Lockbox account fee | Low |
| Customer effort | Scan QR | Use right VA | Mail cheque | Click approve |
| Best for | Swiss B2B + B2C invoicing | High-volume B2B repeat | Insurance, healthcare, gov | Swiss recurring billing |

## Hybrid strategies

- QR-bill default + VA upsell for high-volume B2B (see [[../decisions/0005-virtual-accounts-vs-qr-iban]])
- eBill as digital channel for QR-bill data
- Lockbox as legacy fallback for paper-only payers

## Linked

[[../processes/qr-bill-receivable]] · [[../processes/ar-reconciliation]] · [[../decisions/0005-virtual-accounts-vs-qr-iban]]
