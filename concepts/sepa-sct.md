# SEPA Credit Transfer (SCT)

EUR batch credit transfer scheme. Pan-eurozone + 36 SEPA countries (incl CH, UK, NO).

## Properties

- Settlement: D+1 (next business day, often same-day in practice)
- Max amount: no scheme cap (some PSP caps)
- IBAN + BIC routing (BIC optional intra-SEPA since 2016)
- ISO 20022 native (pain.001 / pacs.008 / pacs.002)
- Governed by EPC SCT Rulebook

## Where it clears

- [[t2]] — Eurosystem RTGS for big-bank settlement
- [[eba-step2]] — main retail SCT clearer
- Other ACHs: equensWorldline, Iberpay (ES), STET (FR)

## SEPA principles

- Same price as domestic EUR transfer (Reg 924/2009)
- IBAN-only (BIC must not be required from payer)
- 14-day refund window for unauthorized

## CH context

CH is SEPA participant — Swiss banks send/receive SCT via [[eurosic]] or direct membership.

## Related

[[sct-inst]] · [[sepa-sdd]] · [[t2]] · [[eba-step2]] · [[../operators/epc]]
