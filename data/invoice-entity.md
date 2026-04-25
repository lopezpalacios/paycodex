# Invoice — canonical entity

Stack-agnostic AR invoice model for QR-bill receivable flow.

## Schema

```yaml
entity: Invoice
fields:
  invoiceId:        { type: uuid, required: true }
  invoiceNumber:    { type: string(35), required: true, unique-per-creditor }
  structuredRef:    { type: StructuredRef, required: true }
  status:           { type: InvoiceStatus, required: true }
  customer:         { type: Customer-ref, required: true }
  amount:           { type: decimal(18,2), required: true }
  currency:         { type: ISO4217, required: true, default: CHF }
  vat:              { type: decimal(18,2) }
  issueDate:        { type: date, required: true }
  dueDate:          { type: date, required: true }
  paidDate:         { type: date }
  payments:         { type: list<PaymentApplication> }
  qrBill:           { type: QRBillData }
  ebill:            { type: EBillStatus }
  notes:            { type: string(500) }
  createdAt:        { type: timestamp, required: true }
  updatedAt:        { type: timestamp, required: true }
  version:          { type: int, required: true }

types:
  InvoiceStatus:    { type: enum, values: [Draft, Issued, Sent, PartiallyPaid, Paid, Disputed, Resolved, Overdue, Dunning, WrittenOff, CreditNoted, Reconciled] }
  StructuredRef:
    type:           { type: enum, values: [SWISS_QR_REF_27, ISO_11649_RF, NONE] }
    value:          { type: string }
  PaymentApplication:
    paymentId:      { type: string }
    amount:         { type: decimal(18,2) }
    appliedAt:      { type: timestamp }
    matchType:      { type: enum, values: [STRUCTURED_REF, INVOICE_NUMBER, FUZZY, MANUAL] }
    confidence:     { type: decimal(3,2), description: "0.00-1.00, 1.00 for structured" }
  QRBillData:
    qrIban:         { type: IBAN }
    creditor:       { type: Party }
    debtorOptional: { type: Party }
    amountEditable: { type: bool }
    qrPayloadVersion: { type: string, default: SPC0200 }
```

## Validation rules

- One invoice → one structured reference, never reused
- For QR-IBAN, structuredRef.type must be SWISS_QR_REF_27
- For standard IBAN, structuredRef.type can be ISO_11649_RF or NONE
- Currency CHF for domestic Swiss QR-bill (EUR allowed since CH SEPA participation)

## Lifecycle integration

PaymentApplication appended on each match event from AR engine. Invoice state transitions per [[../states/invoice-lifecycle]].

## Linked

[[qr-bill-payload]] · [[structured-creditor-reference]] · [[../states/invoice-lifecycle]]
