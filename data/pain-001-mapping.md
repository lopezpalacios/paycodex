# pain.001 → Payment entity mapping

Customer-to-bank credit transfer initiation. Corp's outbound.

## Top structure

```
CstmrCdtTrfInitn
├── GrpHdr
└── PmtInf (one or many)
    ├── PmtInfId
    ├── PmtMtd (TRF)
    ├── BtchBookg (true/false)
    ├── PmtTpInf (SvcLvl/Cd: SEPA, LclInstrm/Cd: INST for SCT Inst)
    ├── ReqdExctnDt
    ├── Dbtr / DbtrAcct / DbtrAgt
    ├── ChrgBr (SLEV)
    └── CdtTrfTxInf (one or many per PmtInf)
```

## Field map

| pain.001 path | Payment entity field |
|---|---|
| GrpHdr/MsgId | (channel-level) |
| PmtInf/PmtTpInf/SvcLvl/Cd | rail derived |
| PmtInf/PmtTpInf/LclInstrm/Cd | rail derived (INST = SCT Inst) |
| PmtInf/Dbtr/Nm | debtor.name |
| PmtInf/DbtrAcct/Id/IBAN | debtorAccount.iban |
| PmtInf/DbtrAgt/FinInstnId/BICFI | debtorAgent.bicfi |
| PmtInf/CdtTrfTxInf/PmtId/EndToEndId | endToEndId |
| PmtInf/CdtTrfTxInf/Amt/InstdAmt | amount + currency |
| PmtInf/CdtTrfTxInf/Cdtr/Nm | creditor.name |
| PmtInf/CdtTrfTxInf/CdtrAcct/Id/IBAN | creditorAccount.iban |
| PmtInf/CdtTrfTxInf/RmtInf/Ustrd | remittance.unstructured |

## Validation at ingest

- Schema (XSD)
- Business rules: currency match (EUR for SCT Inst), IBAN format, amount > 0
- Duplicate detection: hash(InstrId + DbtrAcct + Amt + ExctnDt)
- Authorisation file vs entitlements ([[../07-risk-controls]])

## Output

Each CdtTrfTxInf becomes one Payment entity. Hub fans out to per-rail processing.

## Linked

[[payment-entity]] · [[pacs-008-inst-fields]] · [[../03-tech-integration]]
