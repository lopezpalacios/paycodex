# pacs.008.001.10 (CBPR+) — cross-border field map

ISO 20022 cross-border SWIFT MX (replaces MT103). Stricter than SEPA pacs.008.

## Structure (delta vs SEPA pacs.008)

- Same root: `FIToFICstmrCdtTrf > GrpHdr + CdtTrfTxInf`
- One CdtTrfTxInf per message (no batching)
- UETR mandatory
- Structured address mandatory (post Nov 2025 cross-border)
- Charge bearer: OUR / BEN / SHA (vs SEPA's SLEV-only)
- LEI optional but encouraged
- Intermediary agents (up to 3) supported

## Mandatory CBPR+ fields

| Field | Notes |
|---|---|
| GrpHdr/MsgId | Sender-generated |
| CdtTrfTxInf/PmtId/UETR | Mandatory |
| CdtTrfTxInf/IntrBkSttlmAmt | Currency + amount |
| CdtTrfTxInf/IntrBkSttlmDt | Settlement date |
| CdtTrfTxInf/ChrgBr | OUR / BEN / SHA |
| CdtTrfTxInf/Dbtr/Nm | Up to 140 chars |
| CdtTrfTxInf/Dbtr/PstlAdr/StrtNm | Recommended |
| CdtTrfTxInf/Dbtr/PstlAdr/TwnNm | **Mandatory** Nov 2025 |
| CdtTrfTxInf/Dbtr/PstlAdr/Ctry | **Mandatory** Nov 2025 |
| CdtTrfTxInf/DbtrAcct/Id (IBAN or other) | |
| CdtTrfTxInf/DbtrAgt/FinInstnId/BICFI | |
| CdtTrfTxInf/IntrmyAgt1/2/3 | Optional, structured |
| CdtTrfTxInf/CdtrAgt/FinInstnId/BICFI | |
| CdtTrfTxInf/Cdtr/Nm | |
| CdtTrfTxInf/Cdtr/PstlAdr/TwnNm | **Mandatory** Nov 2025 |
| CdtTrfTxInf/Cdtr/PstlAdr/Ctry | **Mandatory** Nov 2025 |
| CdtTrfTxInf/CdtrAcct/Id | IBAN or other |
| CdtTrfTxInf/Purp/Cd | ISO ExternalPurpose code |
| CdtTrfTxInf/RmtInf/Strd or Ustrd | Structured preferred |

## CBPR+ vs SEPA pacs.008 differences

| Aspect | SEPA SCT | CBPR+ |
|---|---|---|
| Currency | EUR | Any |
| ChrgBr | SLEV only | OUR/BEN/SHA |
| Address | Optional structured | Mandatory structured (post Nov 2025) |
| Intermediaries | 0 | 0-3 |
| Settlement | Single CSM | Correspondent chain |
| UETR | Optional | Mandatory |

## Migration coexistence (now → Nov 2025)

- Cross-border MT103 retired Nov 2025
- During coexistence: receiving bank may still need MT — sending bank's gateway (or SWIFT) translates MX→MT
- Loss of data on translation — esp structured fields
- Banks pushing all corp clients to native MX before deadline

## Linked

[[../concepts/iso-20022]] · [[../concepts/swift]] · [[swift-mt-to-mx-mapping]] · [[../processes/originate-cross-border-wire]]
