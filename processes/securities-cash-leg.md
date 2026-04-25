# Securities settlement cash leg — L2

DvP settlement via T2S (EUR), SIC (CHF), CREST/CHAPS (GBP). Cash leg of every trade settlement.

## Actors

- **Trading parties** — buyer, seller (or their custodians / brokers)
- **CSDs** — [[../operators/euroclear]] / [[../operators/clearstream]] / SIX SIS / CREST
- **CCP** (if cleared) — Eurex Clearing, LCH, Cboe Clear
- **T2S** — settlement platform for EUR
- **Cash accounts** — DCA at NCB (T2S) or operating account (other rails)

## Sequence (T2S DvP Model 1, cleared)

```mermaid
sequenceDiagram
    autonumber
    participant Buyer
    participant CCP
    participant Custodian as Buyer Custodian
    participant CSD1 as Buyer CSD
    participant T2S
    participant CSD2 as Seller CSD
    participant SCustodian as Seller Custodian
    participant Seller

    Buyer->>CCP: trade
    CCP->>CCP: novation, netting per ISIN per day
    CCP->>Custodian: settlement instruction (sese.023)
    Custodian->>CSD1: matching instruction
    Seller->>CCP: trade (other side)
    SCustodian->>CSD2: matching instruction
    CSD1->>T2S: send instruction
    CSD2->>T2S: send instruction
    T2S->>T2S: match
    T2S->>T2S: check securities at CSD2 + cash at Buyer DCA
    T2S->>T2S: atomic transfer (DvP Model 1)
    T2S-->>CSD1: settled (sese.025 confirmation)
    T2S-->>CSD2: settled (sese.025 confirmation)
    Custodian-->>Buyer: account update
    SCustodian-->>Seller: account update
```

## Cash leg specifics

- Buyer's DCA debited
- Seller's (or CCP's) DCA credited
- Both legs simultaneous
- Auto-collateralization fires if buyer DCA short (pre-pledged securities convert to credit)

## Pre-settlement checks

- Securities position at seller CSD ≥ trade qty
- Cash position at buyer DCA ≥ trade value (or auto-coll capacity)
- Matching: trade details agree both sides
- Mandatory data: ISIN, qty, value, settlement date, parties, place of settlement

## Failure modes

- **No matching counterparty instruction** — trade unmatched, cannot settle
- **Insufficient securities** — seller fail
- **Insufficient cash** — buyer fail (rare with auto-coll)
- **Bilateral cancellation**

## CSDR cash penalties

- Daily penalty on failing party until settled
- See [[../concepts/csdr]]

## T+1 transition

- US T+1 since May 2024
- EU T+1 target Oct 2027
- Squeezes pre-matching, FX, funding workflow

## Linked

[[../concepts/dvp]] · [[../concepts/t2s]] · [[../concepts/csdr]] · [[../states/settlement-instruction-lifecycle]] · [[../data/sese-messages]]

## On-chain equivalent

See [`paycodex-onchain` use case 031 — Atomic DvP](https://github.com/lopezpalacios/paycodex-onchain/blob/main/use-cases/031-atomic-dvp.md). Runnable contract in [`paycodex-factory/contracts/31-atomic-dvp.sol`](https://github.com/lopezpalacios/paycodex-factory/blob/main/contracts/31-atomic-dvp.sol). DvP atomicity moves from T2S platform to single Ethereum-style transaction; settlement risk eliminated by reverting if either leg fails.
