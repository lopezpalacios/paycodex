# sese — Securities Settlement messages

ISO 20022 securities settlement message family. Used between custodians, CSDs, T2S.

## Key messages

| Message | Purpose | Replaces |
|---|---|---|
| sese.020 | Securities Settlement Transaction Audit Report | (new) |
| sese.022 | Securities Settlement Transaction Status Advice | MT548 |
| sese.023 | Securities Settlement Transaction Instruction | MT540/541/542/543 |
| sese.024 | Securities Settlement Transaction Status Query | (new) |
| sese.025 | Securities Settlement Transaction Confirmation | MT544/545/546/547 |
| sese.027 | Securities Settlement Transaction Modification Request | (new) |
| sese.028 | Securities Settlement Transaction Cancellation Request | MT540 cancellation |
| sese.030 | Securities Settlement Transaction Allegement Notification | (new) |

## Settlement instruction (sese.023) — key fields

```
SctiesSttlmTxInstr
├── TxId
├── SttlmTpAndAddtlParams
│   ├── SctiesMvmntTp (DELI / RECE)
│   ├── Pmt (APMT / FREE / VPAY) — DVP / FOP / RVP
│   └── SctiesSttlmTxId
├── TradDtls
│   ├── TradDt
│   ├── SttlmDt (intended settlement date)
│   └── DealPric
├── FinInstrmId
│   ├── ISIN
│   └── Othr
├── QtyAndAcctDtls
│   ├── SttlmQty
│   └── SfkpgAcct (custody account)
├── SttlmParams (matching opt, prty)
├── DlvrgSttlmPties / RcvgSttlmPties (counterparty)
└── SttlmAmt (cash leg currency + amount for DvP)
```

## Cash leg flag

`Pmt` field:
- **APMT** — Against Payment (DvP)
- **FREE** — Free of Payment (FoP)
- **VPAY** — Versus Payment (with Free + value-added)

DvP requires APMT = `APMT`.

## Linked

[[../concepts/dvp]] · [[../processes/securities-cash-leg]] · [[../states/settlement-instruction-lifecycle]] · [[iso20022/README]]
