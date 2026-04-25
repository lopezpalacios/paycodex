# Structured creditor reference

Two formats relevant for Swiss + cross-border AR:

## Swiss QR Reference (QRR)

- 27 digits exactly
- Mod-10 recursive check digit (last digit)
- Used with QR-IBAN only
- Replaces legacy ESR/ISR reference (compatible structure)

### Mod-10 recursive algorithm

```python
TABLE = [0, 9, 4, 6, 8, 2, 7, 1, 3, 5]

def qrr_check_digit(digits_26: str) -> int:
    carry = 0
    for d in digits_26:
        carry = TABLE[(carry + int(d)) % 10]
    return (10 - carry) % 10

def is_valid_qrr(ref: str) -> bool:
    if len(ref) != 27 or not ref.isdigit():
        return False
    return qrr_check_digit(ref[:26]) == int(ref[26])
```

### Composition

26 digits = creditor's choice. Common patterns:

- Customer ID (10) + invoice number (10) + zero-pad (6)
- Pure sequential
- Encoded date + invoice number

## ISO 11649 RF (Structured Creditor Reference)

- Format: `RF<2-digit-check><up to 21 alphanumeric>`
- Mod-97 check (similar to IBAN)
- Pan-European, used in SCT remittance
- Used with standard IBAN (NOT QR-IBAN)

### Algorithm

```python
def iso_11649_check(ref_body: str) -> str:
    payload = ref_body + "RF00"  # placeholder
    numeric = "".join(str(ord(c) - 55) if c.isalpha() else c for c in payload)
    check = 98 - (int(numeric) % 97)
    return f"RF{check:02d}{ref_body}"

def is_valid_iso_11649(ref: str) -> bool:
    if not ref.startswith("RF"): return False
    rotated = ref[4:] + ref[:4]
    numeric = "".join(str(ord(c) - 55) if c.isalpha() else c for c in rotated)
    return int(numeric) % 97 == 1
```

## Mapping in pacs.008 / camt.054

- `RmtInf/Strd/CdtrRefInf/Ref` carries the reference
- `RmtInf/Strd/CdtrRefInf/Tp/CdOrPrtry/Cd` carries type (SCOR or proprietary)
- For QRR — proprietary: `<Prtry>QRR</Prtry>`

## Linked

[[invoice-entity]] · [[qr-bill-payload]] · [[../processes/ar-reconciliation]]
