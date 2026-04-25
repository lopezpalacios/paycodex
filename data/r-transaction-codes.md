# R-transaction codes (SDD)

ISO 20022 ExternalReturnReason / ExternalStatusReason code list. SDD-relevant subset.

## Pre-settlement (Reject)

| Code | Meaning |
|---|---|
| AG01 | Transaction forbidden |
| AG02 | Bank operation code invalid |
| AM05 | Duplicate |
| BE05 | Unrecognized initiating party (CID issue) |
| FF05 | Reason not specified |
| MD02 | Mandate missing required information |

## Post-settlement (Return)

| Code | Meaning | Window |
|---|---|---|
| AC01 | Incorrect account number | 5 banking days |
| AC04 | Closed account | 5 banking days |
| AC06 | Blocked account | 5 banking days |
| AC13 | Debtor account type missing or invalid | 5 banking days |
| AM04 | Insufficient funds | 5 banking days |
| MD07 | End customer deceased | 5 banking days |
| RR01 | Regulatory reason | 5 banking days |

## Refund (Core 8-week)

| Code | Meaning |
|---|---|
| MS02 | Not specified by customer | (no questions asked) |
| MS03 | Not specified |
| MD06 | Refund per debtor request |

## Refund (unauthorized 13-month)

| Code | Meaning |
|---|---|
| MD01 | No valid mandate |
| MS02 | Not specified by customer (unauthorized) |

## B2B specifics

- No 8-week refund right
- B2B mandate must be confirmed at debtor PSP
- Refund requires debtor PSP cooperation, much narrower

## Implementation note

R-code handling = state machine extension on Collection entity. Each R-tx triggers:

- Reverse creditor credit
- Hold against creditor exposure limit
- Customer notification
- Audit log
- Possible re-collection (if AM04 — NSF — common)

## Linked

[[../processes/sdd-r-transactions]] · [[../runbooks/r-transaction-handling]] · [[pacs-003-fields]]
