# Securities Settlement Instruction — entity

Stack-agnostic shape for one settlement instruction.

## Schema

```yaml
entity: SettlementInstruction
fields:
  instructionId:    { type: uuid, required: true }
  txReference:      { type: string(35), required: true }
  status:           { type: SettlementStatus, required: true }
  movement:         { type: enum, values: [DELIVER, RECEIVE] }
  settlementType:   { type: enum, values: [APMT_DvP, FREE_FoP, VPAY] }
  isin:             { type: string(12), required: true }
  quantity:         { type: decimal(18,5), required: true }
  tradeDate:        { type: date, required: true }
  intendedSettlementDate: { type: date, required: true }
  actualSettlementDate: { type: date }
  cashAmount:       { type: decimal(18,2) }
  cashCurrency:     { type: ISO4217 }
  custodyAccount:   { type: string(35), required: true }
  cashAccount:      { type: string(35) }
  counterparty:     { type: Party, required: true }
  csd:              { type: enum, values: [EUROCLEAR_BANK, CLEARSTREAM_LUX, CLEARSTREAM_FFM, CSD_FR_ESES, MONTE_TITOLI, IBERCLEAR, SIS, CREST, OTHER] }
  cashRail:         { type: enum, values: [T2S_DCA, SIC, CHAPS, FREE] }
  failPenalty:      { type: list<DailyPenalty> }
  createdAt:        { type: timestamp, required: true }
  updatedAt:        { type: timestamp, required: true }
  version:          { type: int, required: true }

types:
  SettlementStatus: { type: enum, values: [Created, Sent, Pending, Matched, Validated, Settling, Settled, Failed, Cancelled, Expired] }
  DailyPenalty:
    date:           { type: date }
    rate:           { type: decimal(6,4), description: bp/day }
    amount:         { type: decimal(18,2) }
    direction:      { type: enum, values: [PAID, RECEIVED] }
```

## Validation

- ISIN: ISO 6166 (12 chars, country code + national + check)
- Settlement date business-day-valid in CSD calendar
- For DvP: cashAmount + cashCurrency required

## Linked

[[sese-messages]] · [[../states/settlement-instruction-lifecycle]] · [[../concepts/dvp]]
