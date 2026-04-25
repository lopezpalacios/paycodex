# QR-bill

Swiss invoice format. Replaced ISR (red) and IS (orange) payment slips Oct 2022.

## Anatomy

- Standardized A4 invoice + payment section
- Swiss QR Code containing structured payment data
- IBAN or [[qr-iban]] (latter for structured creditor reference)
- Optional structured creditor reference (mod-97, ISO 11649) or no reference

## Why it matters

- Eliminates manual data entry — phone scans QR, fills payment
- Structured reference auto-reconciles AR (vs free-text remittance)
- All Swiss banks must support
- Killed off ISR/IS payment slips (2022 sunset)

## Tech

- QR data format published by SIX
- Validated by banks during payment initiation
- Embedded in pain.001 via structured remittance / creditor reference fields

## AR impact

- Structured reference = perfect match to invoice in ERP
- Replaces lockbox + manual matching workflows in CH
- See [[../02-products]] receivables, [[virtual-accounts]] (similar concept)

## Related

[[qr-iban]] · [[ebill]] · [[sic]]
