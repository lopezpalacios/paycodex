# Payment rails — CH/EU/UK matrix

| Rail | CCY | Type | SLA | Settlement | Format | Operator |
|---|---|---|---|---|---|---|
| [[../concepts/sic]] | CHF | RTGS | Real-time | Central bank money | ISO 20022 | SIX / SNB |
| [[../concepts/sic-ip]] | CHF | Instant | <10s | Central bank money | ISO 20022 | SIX / SNB |
| [[../concepts/eurosic]] | CHF/EUR | Bridge | Variable | Correspondent | ISO 20022 / SEPA | SIX |
| [[../concepts/sepa-sct]] | EUR | Batch credit | D+1 | Net via CSM | ISO 20022 | EPC, multiple CSMs |
| [[../concepts/sct-inst]] | EUR | Instant | <10s | RTGS via TIPS / RT1 | ISO 20022 | EPC, TIPS / RT1 |
| [[../concepts/sepa-sdd]] | EUR | Direct debit | D-1 / D | Net via CSM | ISO 20022 | EPC |
| [[../concepts/t2]] | EUR | RTGS | Real-time | Central bank money | ISO 20022 | Eurosystem |
| [[../concepts/chaps]] | GBP | RTGS | Real-time | Central bank money | ISO 20022 | BoE |
| [[../concepts/bacs]] | GBP | Batch | 3-day cycle | Net | Bacs Standard 18 | Pay.UK |
| [[../concepts/fps]] | GBP | Instant | <2h (typically <10s) | Multi-cycle DNS | FPS proprietary | Pay.UK |

## Pricing parity rules

- SEPA: SCT Inst price ≤ SCT (IPR mandate)
- SEPA: cross-border EUR = domestic EUR (Reg 924/2009)
- CH: SIC + SIC IP — no statutory parity, market-set
- UK: FPS + Bacs — market-set

## Sanctions paradigm

- Instant rails (SCT Inst / SIC IP / FPS): daily customer screening (per [[../regulations/instant-payments-regulation]] for SEPA; CH / UK following pattern)
- Batch + RTGS: per-transaction screening
- Cross-border: per-transaction full screening + WTR data validation

## Linked

[[direct-debit-matrix]] · [[instant-payments-matrix]] · [[../README]]
