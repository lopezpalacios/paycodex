# QR-IBAN

Special Swiss IBAN range used to signal QR-bill with structured creditor reference.

## How to spot

- IBAN with QR-IID — bank identifier in range **30000-31999**
- Same checksum rules as standard IBAN (mod-97)
- Only valid with structured creditor reference (27 digits, mod-10 check)

## Why separate range

- Routing flag — bank knows to expect/require structured reference
- Backwards compat with old ISR processing logic
- One legal-entity bank can have both regular IBAN and QR-IBAN

## Validation rules

- Standard IBAN mod-97 ✓
- IID in 30000-31999 ✓
- Reference present and mod-10 valid ✓

Critical for payment hub validators.

## Related

[[qr-bill]] · [[sic]]
