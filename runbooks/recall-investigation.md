# Runbook: payment recall / investigation

**Scenario**: customer reports payment sent in error, wrong amount, or duplicate.

## SCT Inst is irrevocable

- Settlement final once CSM confirms
- "Recall" is a request to beneficiary, not a reversal
- Beneficiary cooperation required

## Process

1. Customer raises ticket via service team ([[../05-relationships]])
2. Ops creates investigation case
3. Send camt.056 (FI to FI Payment Cancellation Request) or pacs.028 to beneficiary PSP
4. Beneficiary PSP contacts beneficiary, asks for return
5. If agreed: beneficiary PSP sends pacs.004 (return) — new payment back to originator
6. If refused: customer informed, dispute escalated

## Timing

- Customer raises within hours: high recovery rate
- Customer raises after days: low — funds usually moved
- Fraudulent: police report path, not just recall

## Cross-border note

For cross-border SWIFT wires, MT192 / MT196 used — same logic, different format.

## Reg / scheme rules

- EPC SCT Recall scheme rulebook
- Cannot force refund — beneficiary must agree
- Specific exception: fraudulent inducement (BEC) scenarios under PSD3 push payment scam protection (in development)

## Linked

[[../concepts/sct-inst]] · [[../processes/originate-sct-inst]]
