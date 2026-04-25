# pacs.008.001 (SCT Inst variant) — field map

Inter-PSP message carrying the credit transfer. ISO 20022 XML.

## Top structure

```
FIToFICstmrCdtTrf
├── GrpHdr
│   ├── MsgId
│   ├── CreDtTm
│   ├── NbOfTxs
│   ├── SttlmInf (SttlmMtd: CLRG, ClrSys.Cd: TIPS / RT1 / etc)
│   └── InstgAgt / InstdAgt
└── CdtTrfTxInf (one per tx for inst)
    ├── PmtId (InstrId, EndToEndId, TxId, UETR)
    ├── PmtTpInf (SvcLvl: SEPA / INST, LclInstrm: INST, CtgyPurp)
    ├── IntrBkSttlmAmt (currency, amount)
    ├── IntrBkSttlmDt
    ├── ChrgBr (SLEV for SEPA)
    ├── Dbtr (Nm, PstlAdr, Id)
    ├── DbtrAcct (Id.IBAN, Ccy)
    ├── DbtrAgt (FinInstnId.BICFI)
    ├── CdtrAgt
    ├── Cdtr
    ├── CdtrAcct
    ├── Purp (Cd or Prtry)
    └── RmtInf (Ustrd | Strd)
```

## Field map (subset)

| pacs.008 path | Type | Payment entity field | Notes |
|---|---|---|---|
| GrpHdr/MsgId | string(35) | (header) | PSP-generated |
| GrpHdr/CreDtTm | ISODateTime | createdAt | UTC |
| CdtTrfTxInf/PmtId/EndToEndId | string(35) | endToEndId | echo from pain.001 |
| CdtTrfTxInf/PmtId/UETR | UUID | uetr | mandatory |
| CdtTrfTxInf/PmtTpInf/SvcLvl/Cd | string | (rail) | SEPA |
| CdtTrfTxInf/PmtTpInf/LclInstrm/Cd | string | (rail) | INST |
| CdtTrfTxInf/IntrBkSttlmAmt | currency+amount | amount, currency | EUR for SCT Inst |
| CdtTrfTxInf/Dbtr/Nm | string(140) | debtor.name | post-CBPR+ structured pref |
| CdtTrfTxInf/Dbtr/PstlAdr/TwnNm | string(35) | debtor.address.townName | mandatory CBPR+ |
| CdtTrfTxInf/Dbtr/PstlAdr/Ctry | ISO3166 | debtor.address.country | mandatory CBPR+ |
| CdtTrfTxInf/DbtrAcct/Id/IBAN | IBAN | debtorAccount.iban |  |
| CdtTrfTxInf/DbtrAgt/FinInstnId/BICFI | BIC | debtorAgent.bicfi |  |
| CdtTrfTxInf/Cdtr/Nm | string(140) | creditor.name |  |
| CdtTrfTxInf/CdtrAcct/Id/IBAN | IBAN | creditorAccount.iban |  |
| CdtTrfTxInf/Purp/Cd | string(4) | purposeCode | ISO ExternalPurpose |
| CdtTrfTxInf/RmtInf/Ustrd | string(140) | remittance.unstructured | up to 140 chars total |

## Key constraints (SCT Inst)

- One CdtTrfTxInf per message (no batches)
- SttlmMtd = CLRG (clearing), ClrSys.Cd = scheme code (TIPS/RT1)
- Currency = EUR
- ChrgBr = SLEV (SEPA scheme rule)
- Tx and total settlement complete in seconds

## Schema

XSD: `pacs.008.001.10` (CBPR+ / current SCT Inst rulebook). Track EPC scheme rulebook for version updates.

## Linked

[[payment-entity]] · [[pacs-002-status]] · [[../concepts/iso-20022]] · [[../concepts/sct-inst]]
