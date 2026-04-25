# pacs.009 — Financial Institution Credit Transfer

Bank-to-bank credit transfer, used in RTGS rails. Replaces legacy MT202 / MT202 COV.

## Variants

- **pacs.009 CORE** — direct bank-to-bank
- **pacs.009 ADV (cover)** — cover for underlying customer payment
- **pacs.009 COV (cover with detail)** — embeds underlying customer payment data

## Top structure

```
FICdtTrf
├── GrpHdr
└── CdtTrfTxInf (one per tx)
    ├── PmtId (InstrId, EndToEndId, TxId, UETR)
    ├── PmtTpInf (LclInstrm, CtgyPurp)
    ├── IntrBkSttlmAmt
    ├── IntrBkSttlmDt
    ├── SttlmTmReq (settlement time request)
    ├── InstgAgt
    ├── InstdAgt
    ├── Dbtr (the bank)
    ├── DbtrAcct (settlement account)
    ├── DbtrAgt
    ├── CdtrAgt (intermediary if any)
    ├── Cdtr (the bank)
    ├── CdtrAcct
    ├── Purp
    └── (cover: UndrlygCstmrCdtTrf)
```

## Use cases

- Treasury bank-to-bank transfers (no end customer)
- Cover payments where underlying customer pacs.008 routes via different chain
- RTGS direct participant settlement
- Liquidity management between bank's own accounts at different central banks

## RTGS rail mapping

- [[../concepts/sic]]: pacs.008 / pacs.009 native
- [[../concepts/t2]]: pacs.008 / pacs.009 native (post Mar 2023 consolidation)
- [[../concepts/chaps]]: pacs.008 / pacs.009 native (post 2023 ISO 20022 migration)

## Linked

[[pacs-008-cbpr-fields]] · [[../concepts/iso-20022]] · [[../processes/originate-rtgs-wire]]
