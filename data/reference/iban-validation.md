# IBAN validation

Validation rules for International Bank Account Numbers.

## Structure

`<CC><DD><BBAN>` — country (2) + check (2) + Basic BAN (variable)

## Algorithm (mod-97)

1. Move first 4 chars to end
2. Replace letters with digits: A=10, B=11, ..., Z=35
3. Compute integer mod 97
4. Valid if remainder = 1

## Length per country (subset)

| Country | Length | Example |
|---|---|---|
| AT | 20 | AT611904300234573201 |
| BE | 16 | BE68539007547034 |
| CH | 21 | CH9300762011623852957 |
| DE | 22 | DE89370400440532013000 |
| ES | 24 | ES9121000418450200051332 |
| FR | 27 | FR1420041010050500013M02606 |
| GB | 22 | GB29NWBK60161331926819 |
| IT | 27 | IT60X0542811101000000123456 |
| LU | 20 | LU280019400644750000 |
| NL | 18 | NL91ABNA0417164300 |
| PT | 25 | PT50000201231234567890154 |

Full list: SWIFT IBAN registry (~80 countries).

## Swiss QR-IBAN

- Same structure as standard IBAN
- IID (positions 5-9 in BBAN) in range **30000-31999** = QR-IBAN
- See [[../../concepts/qr-iban]]

## Validation pipeline

```python
def is_valid_iban(iban: str) -> bool:
    s = iban.replace(" ", "").upper()
    if not (15 <= len(s) <= 34):
        return False
    if not s[:2].isalpha():
        return False
    if not s[2:4].isdigit():
        return False
    rearranged = s[4:] + s[:4]
    numeric = "".join(str(ord(c) - 55) if c.isalpha() else c for c in rearranged)
    return int(numeric) % 97 == 1
```

## Per-country length check

Always check both mod-97 AND country-specific length. Mod-97 alone allows malformed IBANs of wrong length.

## Linked

[[../../concepts/qr-iban]] · [[../payment-entity]]
