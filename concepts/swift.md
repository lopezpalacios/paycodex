# SWIFT

Society for Worldwide Interbank Financial Telecommunication. Messaging network — not a payment rail itself.

## Products

- **FIN** — message switching (MT messages)
- **FileAct** — bulk file transfer
- **InterAct** — real-time messaging
- **gpi** — global payments innovation, end-to-end tracking with UETR
- **Alliance Lite2** — cloud SWIFT, no on-prem infra

## Corp connectivity models

- **SCORE** — corp-to-bank, multi-bank
- **MA-CUG** — closed user group with single bank

## Key MT messages (legacy)

- MT101 payment init → being replaced by pain.001 ([[iso-20022]])
- MT103 customer credit transfer → pacs.008
- MT940 EOD statement → camt.053
- MT942 intraday → camt.052
- MT192/196 recall

## Migration

SWIFT MT → MX (ISO 20022) deadline Nov 2025.

## Security

SWIFT CSP (Customer Security Programme) mandatory controls. See [[07-risk-controls]].

## Related

[[iso-20022]] · [[wire]] · [[03-tech-integration]]
