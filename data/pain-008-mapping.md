# pain.008 — Customer Direct Debit Initiation

Corp-to-creditor-PSP message. Submits batch of collections. Each collection references a [[mandate-entity]] via UMR.

## Top structure

```
CstmrDrctDbtInitn
├── GrpHdr
└── PmtInf (one per CSM submission group)
    ├── PmtInfId
    ├── PmtMtd (DD)
    ├── PmtTpInf (SvcLvl/Cd: SEPA, LclInstrm/Cd: CORE | B2B, SeqTp: FRST | RCUR | OOFF | FNAL)
    ├── ReqdColltnDt
    ├── Cdtr / CdtrAcct / CdtrAgt
    ├── ChrgBr (SLEV)
    ├── CdtrSchmeId (Id.PrvtId.Othr.Id = CID)
    └── DrctDbtTxInf (one per collection)
        ├── PmtId (InstrId, EndToEndId, UETR)
        ├── InstdAmt
        ├── DrctDbtTx
        │   └── MndtRltdInf (MndtId = UMR, DtOfSgntr, AmdmntInd, AmdmntInfDtls)
        ├── DbtrAgt (FinInstnId.BICFI)
        ├── Dbtr / DbtrAcct
        ├── Purp (Cd)
        └── RmtInf (Ustrd | Strd)
```

## Field map (subset)

| pain.008 path | Type | Maps to |
|---|---|---|
| PmtInf/PmtTpInf/SvcLvl/Cd | string | rail (SEPA) |
| PmtInf/PmtTpInf/LclInstrm/Cd | string | variant (CORE / B2B) |
| PmtInf/PmtTpInf/SeqTp | string | sequence (FRST/RCUR/OOFF/FNAL) |
| PmtInf/CdtrSchmeId/Id/PrvtId/Othr/Id | string | Mandate.cid |
| DrctDbtTxInf/DrctDbtTx/MndtRltdInf/MndtId | string(35) | Mandate.umr |
| DrctDbtTxInf/DrctDbtTx/MndtRltdInf/DtOfSgntr | date | Mandate.signatureDate |
| DrctDbtTxInf/InstdAmt | currency+amount | Collection.amount |
| DrctDbtTxInf/Dbtr/Nm | string(140) | Mandate.debtor.name |
| DrctDbtTxInf/DbtrAcct/Id/IBAN | IBAN | Mandate.debtorAccount.iban |
| DrctDbtTxInf/PmtId/EndToEndId | string(35) | Collection.endToEndId |

## Validation at ingest

- Schema (pain.008.001.08 typically)
- UMR exists in mandate store, status appropriate
- Sequence type matches mandate state (FRST only on first use, RCUR on recurring)
- Amount ≤ mandate amount cap if set
- ReqdColltnDt ≥ now + lead time (D-1 post-2016)
- Pre-notification evidence per scheme rule (creditor responsibility)

## Linked

[[mandate-entity]] · [[pacs-003-fields]] · [[../processes/originate-sdd]]
