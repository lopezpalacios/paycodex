# SWIFT MT ↔ MX field mapping

Legacy SWIFT MT (FIN) to ISO 20022 MX. Critical reference for migration period (now-Nov 2025) and for translation gateways.

## Major message replacements

| MT | MX | Purpose |
|---|---|---|
| MT101 | pain.001 | Customer credit transfer initiation |
| MT103 | pacs.008 | Customer credit transfer (FI to FI) |
| MT202 | pacs.009 | Bank-to-bank credit transfer |
| MT202 COV | pacs.009 ADV | Cover payment |
| MT900 | camt.054 | Debit confirmation |
| MT910 | camt.054 | Credit notification |
| MT940 | camt.053 | Statement (EOD) |
| MT942 | camt.052 | Intraday statement |
| MT192/195 | camt.056 | Cancellation request |
| MT196/199 | camt.029 | Cancellation answer |

## MT103 → pacs.008 field map (subset)

| MT103 field | pacs.008 path | Notes |
|---|---|---|
| :20: Sender ref | GrpHdr/MsgId | Up to 35 chars |
| :32A: Value date / CCY / amount | IntrBkSttlmDt + IntrBkSttlmAmt | Split into structured |
| :50K: Ordering customer | Dbtr/Nm + PstlAdr | Free-text → structured |
| :52A: Ordering institution | DbtrAgt/FinInstnId/BICFI | |
| :53A: Sender's correspondent | InstgAgt/FinInstnId | |
| :56A: Intermediary | IntrmyAgt1 | |
| :57A: Account with institution | CdtrAgt | |
| :59: Beneficiary | Cdtr/Nm + CdtrAcct + PstlAdr | |
| :70: Remittance information | RmtInf/Ustrd | Up to 140 chars |
| :71A: Charge bearer | ChrgBr | OUR/BEN/SHA |
| :72: Sender to receiver info | Various | Often misused — translation tricky |
| :77B: Regulatory reporting | InstrForCdtrAgt or InstrForNxtAgt | |

## Translation losses

- Free-text :50K name+address → structured Dbtr.Nm + PstlAdr (TwnNm + Ctry mandatory post Nov 2025)
- :72 codeword content often unstructured — may not survive round-trip
- Address truncation (35 char lines) → MX 70 chars + structured fields

## Migration patterns

1. **Native MX**: bank sends + receives MX directly (modern target state)
2. **Hybrid via translation gateway**: bank speaks MX internally, gateway translates to MT for legacy receivers
3. **MT-only**: legacy bank, must be off rail by Nov 2025 for cross-border

## Linked

[[pacs-008-cbpr-fields]] · [[../concepts/swift]] · [[../concepts/iso-20022]]
