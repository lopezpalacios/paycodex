# Originate cross-border wire — L2

End-to-end cross-border SWIFT credit transfer. CHF/EUR/GBP outbound to any global counterparty. Different from domestic [[../concepts/wire]] — multi-bank correspondent chain.

## Actors

- **Originator** (corp customer) — initiates
- **Sending bank** (originator's bank) — debits originator
- **Intermediary banks** (correspondent chain) — 0-3 hops
- **Beneficiary bank** — credits beneficiary
- **CLS / nostro / vostro** layer — currency settlement
- **gpi tracker** — UETR-based tracking layer

## Sequence

```mermaid
sequenceDiagram
    autonumber
    participant Orig as Originator
    participant SBank as Sending bank
    participant IB1 as Intermediary 1
    participant IB2 as Intermediary 2
    participant BBank as Beneficiary bank
    participant Bene as Beneficiary
    participant Tracker as SWIFT gpi tracker

    Orig->>SBank: pain.001 (or MT101)
    SBank->>SBank: validate, screen, FX (if needed), assign UETR
    SBank->>Tracker: UETR registered
    SBank->>IB1: pacs.008 (or MT103)
    IB1->>Tracker: status update
    IB1->>IB2: pacs.008
    IB2->>Tracker: status update
    IB2->>BBank: pacs.008
    BBank->>Tracker: credited
    BBank->>Bene: account credit
    BBank-->>IB2: pacs.002 (settled)
    IB2-->>IB1: pacs.002
    IB1-->>SBank: pacs.002
    SBank-->>Orig: pain.002 / camt.054
    SBank->>Tracker: closed
```

## Currency settlement layer (parallel to messaging)

- Each leg between banks settles via correspondent account (nostro at next bank's books)
- Major USD chain: most non-US banks settle USD via JPM Chase / Citi / BNY / BofA (the big USD correspondents)
- EUR chain: T2 if both EU, else correspondent
- CHF chain: SIC if both CH, else correspondent
- FX leg: handled at sending or intermediary depending on payment instructions (charge bearer)

## CBPR+ (ISO 20022 cross-border)

- SWIFT cross-border traffic migrating to MX (pacs.008.001.10) by Nov 2025
- New mandatory fields: structured address (town, country), LEI, structured remittance
- Coexistence period 2023-2025: CBPR+ MX can be sent, banks must convert to MT for non-MX-ready receivers (Translation responsibility)
- After Nov 2025: MT103 cross-border retired

## Charge bearer

| Code | Meaning |
|---|---|
| OUR | Originator pays all charges |
| BEN | Beneficiary pays all charges |
| SHA | Shared (originator pays sending bank, beneficiary pays rest) |

For SEPA: SLEV only.

## Branch points

- Sanctions hit at any leg → block, payment held by that bank
- Bad beneficiary info → manual repair at intermediary or BBank, may delay days
- FX rate dispute → SBank applies pre-disclosed rate
- Compliance queries (KYC/source of funds) by intermediaries → ETA delays

## Latency

- Same-day: only if all parties + cutoffs aligned (often ≤1 hop, major currency)
- Typical: 1-3 business days
- gpi commitment: 50% of gpi payments credited within 30 minutes, 100% within 24 hours (gpi service level)

## Linked

[[gpi-tracking]] · [[../concepts/swift]] · [[../concepts/iso-20022]] · [[../states/cross-border-wire-lifecycle]] · [[../data/pacs-008-cbpr-fields]]
