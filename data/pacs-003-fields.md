# pacs.003 — FI to FI Customer Direct Debit

Inter-PSP SDD message. Carries individual debit between Creditor PSP and Debtor PSP.

## Top structure

```
FIToFICstmrDrctDbt
├── GrpHdr
└── DrctDbtTxInf (one per collection)
    ├── PmtId (InstrId, EndToEndId, TxId, UETR)
    ├── PmtTpInf (SvcLvl, LclInstrm, SeqTp)
    ├── IntrBkSttlmAmt
    ├── IntrBkSttlmDt
    ├── ChrgBr (SLEV)
    ├── DrctDbtTx (MndtRltdInf, CdtrSchmeId)
    ├── CdtrAgt
    ├── Cdtr
    ├── CdtrAcct (creditor settlement account)
    ├── DbtrAgt
    ├── Dbtr
    ├── DbtrAcct
    ├── Purp
    └── RmtInf
```

## Differences vs pain.008

- Inter-bank perspective (no PmtInf grouping)
- Settlement amount + date populated
- Debtor side BIC populated (for routing)
- One DrctDbtTxInf per collection (no batching at message level)

## Routing

- Creditor PSP → CSM → Debtor PSP
- CSM may aggregate into settlement file (depending on operator)
- Pre-settlement validation at debtor PSP (mandate, account)

## Settlement

- For SDD: settlement happens on collection date (D), not at message receipt
- D-1 send window for pre-settlement validation
- Creditor account credited on D, debtor account debited on D

## Linked

[[pain-008-mapping]] · [[r-transaction-codes]] · [[../states/payment-lifecycle]]
