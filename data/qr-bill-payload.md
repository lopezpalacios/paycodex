# QR-bill payload — Swiss QR Code data

Swiss QR Code carries structured payment data. SIX publishes specification "Swiss Implementation Guidelines QR-bill" (current: SPC v2.2 / 2024).

## Field layout (top to bottom of QR data)

| Line | Field | Type | Notes |
|---|---|---|---|
| 1 | QRType | string | "SPC" |
| 2 | Version | string | "0200" or "0210" |
| 3 | CodingType | string | "1" (UTF-8) |
| 4 | IBAN | string(21) | QR-IBAN or standard IBAN |
| 5-11 | Creditor | block | combined-address or structured-address |
| 12-18 | UltimateCreditor | block (optional) | reserved |
| 19 | Amount | decimal | optional (open amount = empty) |
| 20 | AmountCurrency | string(3) | CHF or EUR |
| 21-27 | UltimateDebtor | block (optional) | known payer |
| 28 | ReferenceType | string | "QRR" / "SCOR" / "NON" |
| 29 | Reference | string | 27-digit Swiss or ISO 11649 RF |
| 30 | UnstructuredMessage | string(140) | optional free text |
| 31 | Trailer | string | "EPD" (End Payment Data) |
| 32 | BillInformation | string(140) | optional structured (S1 format) |

## Reference types

- **QRR** — Swiss QR Reference (27 digits, mod-10) — required for QR-IBAN
- **SCOR** — Structured Creditor Reference (ISO 11649 RF) — for standard IBAN with structured ref
- **NON** — no reference (free-text only) — standard IBAN only

## Address format

- Combined: `K` line — single string
- Structured: `S` lines — name, street, building no, postcode, town, country

Structured preferred for ISO 20022 alignment + cross-border resilience.

## Encoding

- QR Code Model 2, Error Correction Level M, max version 25
- UTF-8, max ~997 chars
- Swiss Cross overlay (7mm × 7mm) at center

## Validation pipeline

```python
def validate_qr_payload(lines: list[str]) -> bool:
    if lines[0] != "SPC": return False
    if lines[1] not in ("0200", "0210"): return False
    if not is_valid_iban(lines[3]): return False
    iban = lines[3]
    iid = int(iban[4:9])  # IID position
    is_qr_iban = 30000 <= iid <= 31999
    ref_type = lines[27]
    ref = lines[28]
    if is_qr_iban and ref_type != "QRR":
        return False
    if ref_type == "QRR" and not is_valid_qrr(ref):
        return False
    if ref_type == "SCOR" and not is_valid_iso_11649(ref):
        return False
    return True
```

## Linked

[[invoice-entity]] · [[structured-creditor-reference]] · [[../concepts/qr-bill]] · [[../concepts/qr-iban]]
