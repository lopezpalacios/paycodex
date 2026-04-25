# Commercial card issuance + reconciliation — L2

Per corporate card program: issuance, transaction posting, reconciliation, settlement.

## Issuance flow

```mermaid
sequenceDiagram
    participant Corp
    participant Bank as Issuer Bank
    participant Network as Card Network
    participant Cardholder as Employee
    Corp->>Bank: program setup (limits, MCC restrictions, billing cycle)
    Bank->>Network: BIN allocation, card production order
    Network->>Bank: cards produced
    Bank->>Cardholder: card delivered
    Bank-->>Corp: card list, controls dashboard
```

## Transaction flow

```mermaid
sequenceDiagram
    participant Cardholder
    participant Merchant
    participant Acquirer
    participant Network
    participant Issuer
    Cardholder->>Merchant: pay with card
    Merchant->>Acquirer: auth request
    Acquirer->>Network: auth
    Network->>Issuer: auth request
    Issuer->>Issuer: limit + risk check
    Issuer-->>Network: approve
    Network-->>Acquirer: approve
    Acquirer-->>Merchant: approve
    Note over Merchant,Issuer: settlement T+1 to T+3
    Acquirer->>Network: clearing file
    Network->>Issuer: clearing file
    Issuer->>Corp: settle on cycle (statement)
```

## Reconciliation

- Daily transaction feed to corp ERP / expense system
- Match: card txn → expense report (T&E) or PO (P-card)
- Level III data (line item) where merchant supports
- Disputed txns: chargeback path via network rules

## Settlement to bank

- Statement cycle (typically monthly or 14-day)
- Direct debit ([[../concepts/sepa-sdd]] / [[../concepts/bacs]]) or wire from corp DDA
- Some programs: real-time auto-debit

## Related

[[../concepts/commercial-card]] · [[../concepts/virtual-card]] · [[../concepts/interchange]]
