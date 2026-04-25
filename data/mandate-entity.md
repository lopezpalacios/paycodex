# Mandate — canonical entity

SEPA Direct Debit mandate. Stack-agnostic shape.

## Schema

```yaml
entity: Mandate
fields:
  mandateId:        { type: uuid, required: true, source: creditor-system }
  umr:              { type: string(35), required: true, source: creditor-assigned, unique-per-cid }
  cid:              { type: string(35), required: true }
  type:             { type: enum, values: [SDD_CORE, SDD_B2B] }
  status:           { type: MandateStatus, required: true }
  signatureDate:    { type: date, required: true }
  signatureMethod:  { type: enum, values: [WET, ELECTRONIC, EMANDATE] }
  storageRef:       { type: string, source: document-store-pointer }
  creditor:         { type: Party, required: true }
  debtor:           { type: Party, required: true }
  debtorAccount:    { type: Account, required: true }
  amountCap:        { type: decimal(18,2), description: optional max per collection }
  frequency:        { type: enum, values: [ONEOFF, RECURRENT, MONTHLY, etc.] }
  firstCollectionDate: { type: date }
  lastCollectionDate:  { type: date, source: latest collection settled }
  finalCollectionDate: { type: date, source: FNAL settlement }
  expiryDate:       { type: date, computed: lastCollectionDate + 36 months }
  cancellationDate: { type: date }
  cancellationReason: { type: string(140) }
  amendments:       { type: list<MandateAmendment> }
  createdAt:        { type: timestamp, required: true }
  updatedAt:        { type: timestamp, required: true }
  version:          { type: int, required: true }

types:
  MandateStatus:    { type: enum, values: [Draft, Issued, Active, FirstUsed, Recurring, Amended, Cancelled, Expired, Final, Settled] }
  MandateAmendment:
    amendmentId:    { type: uuid }
    field:          { type: enum, values: [DebtorName, DebtorIBAN, CreditorName, AmountCap, Frequency] }
    oldValue:       { type: string }
    newValue:       { type: string }
    amendedAt:      { type: timestamp }
    reason:         { type: string(140) }
```

## Validation rules

- UMR uniqueness scoped to CID
- IBAN validates per [[reference/iban-validation]]
- For B2B mandates, debtor PSP confirms — additional registration step
- Amendment chain auditable; no destructive overwrites

## Lifecycle integration

State transitions emit events:

- `mandate.issued`
- `mandate.activated`
- `mandate.firstUsed`
- `mandate.amended`
- `mandate.cancelled`
- `mandate.expired`
- `mandate.final`

Subscribed by: collection batch generator, audit, customer comms, mandate dispute service.

## Linked

[[pain-008-mapping]] · [[../states/mandate-lifecycle]] · [[../concepts/sepa-mandate]]
