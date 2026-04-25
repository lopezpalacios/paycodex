# Invoice lifecycle (QR-bill receivable)

State machine for one invoice from issuance to closed.

```mermaid
stateDiagram-v2
    [*] --> Draft: created in ERP
    Draft --> Issued: approved + ref assigned
    Issued --> Sent: delivered (paper / PDF / eBill)
    Sent --> PartiallyPaid: payment < amount, ref match
    Sent --> Paid: payment = amount, ref match
    PartiallyPaid --> Paid: subsequent payment closes balance
    Sent --> Disputed: customer raises issue
    PartiallyPaid --> Disputed
    Disputed --> Resolved: agreement reached
    Resolved --> Paid
    Resolved --> CreditNoted: credit note issued
    Sent --> Overdue: due date passed, unpaid
    Overdue --> Paid: late payment
    Overdue --> Dunning: collection process started
    Dunning --> WrittenOff: bad debt
    Paid --> Reconciled: GL posting confirmed
    CreditNoted --> [*]
    WrittenOff --> [*]
    Reconciled --> [*]
```

## State semantics

| State | Owner | Persisted? | Reversible? |
|---|---|---|---|
| Draft | ERP | Yes | Yes |
| Issued | ERP | Yes | Yes |
| Sent | ERP / billing system | Yes | No |
| PartiallyPaid | AR engine | Yes | Yes |
| Paid | AR engine | Yes | Yes (refund) |
| Disputed | Customer service | Yes | Yes |
| Resolved | Customer service | Yes | No |
| Overdue | Scheduled job | Yes | Yes |
| Dunning | Collections | Yes | Yes |
| WrittenOff | Finance | Yes | No |
| CreditNoted | Finance | Yes | No |
| Reconciled | GL | Yes | No |

## Events emitted

- `invoice.issued`
- `invoice.sent`
- `invoice.payment.applied` (with amount + ref)
- `invoice.disputed`
- `invoice.overdue`
- `invoice.dunning.started`
- `invoice.written-off`
- `invoice.reconciled`

## Linked

[[../processes/qr-bill-receivable]] · [[../processes/ar-reconciliation]] · [[../data/invoice-entity]]
