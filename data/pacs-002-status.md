# pacs.002 — payment status report

Status response from CSM / beneficiary PSP back up the chain.

## Structure

```
FIToFIPmtStsRpt
├── GrpHdr
└── TxInfAndSts
    ├── OrgnlGrpInfAndSts (or OrgnlEndToEndId / OrgnlUETR)
    ├── TxSts (ACSC, ACTC, RJCT, ACSP, etc.)
    └── StsRsnInf (Rsn/Cd, AddtlInf)
```

## Status codes

| Code | Meaning |
|---|---|
| ACCC | Accepted, settlement completed (creditor side) |
| ACSC | Accepted, settlement completed |
| ACSP | Accepted, settlement in process |
| ACTC | Accepted technical validation |
| ACWC | Accepted with change |
| PDNG | Pending |
| RJCT | Rejected |

## Reason codes (ExternalStatusReason)

Common in SCT Inst RJCT:

- AB05 | Timeout creditor
- AB06 | Timeout intermediary
- AC01 | Incorrect account number
- AC04 | Closed account
- AC06 | Blocked account
- AG01 | Transaction forbidden
- AGNT | Agent reason
- AM05 | Duplicate
- BE05 | Unrecognized initiating party
- FF05 | Reason not specified
- RR01 | Regulatory reason

## Mapping to Payment status

- ACSC → Payment.status = Settled
- ACSP → Payment.status = Cleared
- RJCT → Payment.status = Failed (with reason captured)

## Linked

[[pacs-008-inst-fields]] · [[../states/payment-lifecycle]] · [[../runbooks/timeout-handling]]
