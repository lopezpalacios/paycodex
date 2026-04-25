# Wholesale CBDC settlement — L2

Pattern for settling securities or FX leg via wholesale CBDC. Based on [[../concepts/project-helvetia]] live model.

## Sequence (DvP via wholesale CBDC on DLT)

```mermaid
sequenceDiagram
    autonumber
    participant Buyer
    participant SDX as DLT venue (e.g. SDX)
    participant Seller
    participant SNB as Central bank (token issuer)

    Buyer->>SNB: subscribe to wholesale CBDC tokens (debit SIC reserve, credit DLT wallet)
    Seller->>SDX: place tokenized security
    Buyer->>SDX: trade match
    SDX->>SDX: smart contract: atomic swap (security <-> CBDC tokens)
    SDX-->>Buyer: receives security tokens
    SDX-->>Seller: receives CBDC tokens
    Seller->>SNB: redeem CBDC tokens (debit DLT wallet, credit SIC reserve)
```

## Key properties

- Atomic — both legs settle or neither
- Final + immediate
- 24/7 capable (subject to SNB issuance window)
- Programmable: conditional, multi-leg trades possible

## Cash mgmt integration

- Bank holds wallet of wholesale CBDC tokens
- Position counted alongside SIC reserves for liquidity purposes
- Daily reconciliation: DLT balance + SIC balance = total CB money
- New ops dimension: token wallet management, key custody

## Vs traditional T2S DvP

- Traditional: T2S coordinates DvP across CSD + DCA at NCB
- DLT: single platform for both legs, no inter-system messaging
- Reduces operational complexity, requires new tech stack

## Related

[[../concepts/wholesale-cbdc]] · [[../concepts/project-helvetia]] · [[../concepts/dlt-settlement]] · [[securities-cash-leg]]
