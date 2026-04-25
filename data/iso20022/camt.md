# camt — Cash Management

Statements, notifications, investigations.

| Message | Purpose | Replaces |
|---|---|---|
| camt.052 | Bank to Customer Account Report (intraday) | MT942 |
| camt.053 | Bank to Customer Statement (EOD) | MT940 |
| camt.054 | Bank to Customer Debit/Credit Notification | MT900 / MT910 |
| camt.055 | Customer Payment Cancellation Request | MT192 |
| camt.056 | FI to FI Payment Cancellation Request | MT192 / MT195 |
| camt.029 | Resolution of Investigation | MT196 / MT199 |
| camt.060 | Account Reporting Request | MT920 |
| camt.027 | Claim Non Receipt | MT195 / MT199 |

## Investigation flow

- camt.027 to claim non-receipt
- camt.056 to request cancellation
- camt.029 to resolve / respond

## Linked

[[../../processes/originate-cross-border-wire]] · [[../../runbooks/wire-investigation]] · [[../../runbooks/recall-investigation]]
