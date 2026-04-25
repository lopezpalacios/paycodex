# Bacs DDI — entity

UK Direct Debit Instruction. Variant of mandate model with DDG-specific fields.

## Schema

```yaml
entity: BacsDDI
fields:
  ddiId:            { type: uuid, required: true }
  serviceUserNumber: { type: string(6), required: true, source: assigned-by-PSP }
  serviceUserRef:   { type: string(18), required: true, source: SU-assigned }
  status:           { type: BacsDDIStatus, required: true }
  signatureMethod:  { type: enum, values: [PAPER, PAPERLESS_ONLINE, PAPERLESS_PHONE] }
  signatureEvidence: { type: string, description: "audio/IP/scan ref" }
  signatureDate:    { type: date, required: true }
  debtor:           { type: Party, required: true }
  debtorAccount:    { type: BacsAccount, required: true }
  serviceUserName:  { type: string(140), required: true }
  paymentScheme:    { type: enum, values: [BACS_DD] }
  auddiSubmitted:   { type: date }
  auddiAcknowledged: { type: date }
  firstCollectionDate: { type: date }
  lastCollectionDate:  { type: date }
  cancellationDate: { type: date }
  cancellationReason: { type: string(140) }
  createdAt:        { type: timestamp, required: true }
  updatedAt:        { type: timestamp, required: true }
  version:          { type: int, required: true }

types:
  BacsDDIStatus:    { type: enum, values: [Drafted, Signed, Submitted, Active, Used, Amended, Cancelled, Rejected] }
  BacsAccount:
    sortCode:       { type: string(6), pattern: "[0-9]{6}" }
    accountNumber:  { type: string(8), pattern: "[0-9]{8}" }
    bankName:       { type: string(70) }
```

## Validation

- Sort code 6 digits, account number 8 digits (UK domestic format)
- AUDDIS submission within 10 working days of signing (scheme rule)
- SUN active at PSP

## Linked

[[../concepts/bacs]] · [[mandate-entity]] · [[../processes/bacs-dd-mandate-lifecycle]]
