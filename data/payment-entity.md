# Payment — canonical entity

Stack-agnostic shape. Map to ORM, Avro, Protobuf, JSON Schema as needed.

## Schema

```yaml
entity: Payment
fields:
  paymentId:        { type: uuid, required: true, source: bank-generated }
  endToEndId:       { type: string(35), required: true, source: pain.001/CdtTrfTxInf/PmtId/EndToEndId }
  instructionId:    { type: string(35), source: pain.001/CdtTrfTxInf/PmtId/InstrId }
  uetr:             { type: uuid, required: true, source: bank-generated, format: SWIFT-UETR }
  rail:             { type: enum, values: [SCT, SCT_INST, SDD_CORE, SDD_B2B, SIC, SIC_IP, T2, CHAPS, FPS, BACS_DC, BACS_DD, WIRE_SWIFT] }
  amount:           { type: decimal(18,5), required: true }
  currency:         { type: ISO4217, required: true }
  valueDate:        { type: date }
  executionDate:    { type: date }
  debtor:           { type: Party, required: true }
  debtorAccount:    { type: Account, required: true }
  debtorAgent:      { type: Agent }
  creditor:         { type: Party, required: true }
  creditorAccount:  { type: Account, required: true }
  creditorAgent:    { type: Agent }
  remittance:       { type: Remittance }
  purposeCode:      { type: ISO20022-ExternalPurpose }
  categoryPurpose:  { type: ISO20022-CategoryPurpose }
  chargeBearer:     { type: enum, values: [SLEV, SHAR, DEBT, CRED] }
  status:           { type: PaymentStatus, required: true }
  vopResult:        { type: VOPResult }
  screeningResult:  { type: ScreeningResult }
  fraudScore:       { type: decimal(5,2) }
  createdAt:        { type: timestamp, required: true }
  updatedAt:        { type: timestamp, required: true }
  version:          { type: int, required: true }

types:
  Party:
    name:           { type: string(140), required: true }
    identification: { type: PartyId }
    address:        { type: PostalAddress }
    countryOfResidence: { type: ISO3166 }
  Account:
    iban:           { type: IBAN }
    other:          { type: GenericAccount }
    currency:       { type: ISO4217 }
  Agent:
    bicfi:          { type: BIC }
    name:           { type: string(140) }
    address:        { type: PostalAddress }
  Remittance:
    unstructured:   { type: string(140), maxOccurs: many }
    structured:     { type: StructuredRemittance }
  PostalAddress:
    addressType:    { type: enum }
    streetName:     { type: string(70) }
    townName:       { type: string(35), required: true (post-CBPR+) }
    country:        { type: ISO3166, required: true (post-CBPR+) }
    postCode:       { type: string(16) }
  PaymentStatus:    { type: enum, values: [Received, Validated, VOPCheck, ScreeningPending, FraudPending, LimitCheck, Authorized, Reserved, Cleared, Settled, Held, ManualReview, Failed, Rejected, Cancelled, Reconciled] }
  VOPResult:        { type: enum, values: [match, close_match, no_match, not_supported, timeout] }
  ScreeningResult:  { type: enum, values: [clear, hold_party, hold_country, hold_text] }
```

## Validation rules

- IBAN: see [[reference/iban-validation]]
- Currency must be ISO 4217 active
- For SCT / SCT Inst, currency = EUR
- Amount > 0
- For SCT Inst, amount ≤ scheme limit (currently no scheme cap post-IPR, but PSP may set internal cap)
- Town + country mandatory under CBPR+ (Nov 2025)

## Linked

[[pacs-008-inst-fields]] · [[pain-001-mapping]] · [[../states/payment-lifecycle]]
