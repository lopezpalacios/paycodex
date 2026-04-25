# FPS — control catalog

| ID | Control | Frequency | Evidence | Risk |
|---|---|---|---|---|
| C-FPS-COP-01 | CoP check before send | Per tx | API log | Misdirected payment |
| C-FPS-LIM-01 | £1M scheme limit enforcement | Per tx | Limit log | Reg/scheme |
| C-FPS-FBK-01 | Auto-fallback to CHAPS above limit | Per case | Routing log | Customer service |
| C-FPS-SCA-01 | PSD2-equivalent SCA (UK regs) | Per session | SCA event log | Fraud |
| C-FPS-SAN-01 | Per-tx sanctions screening (UK OFSI primary) | Per tx | Engine log | Sanctions |
| C-FPS-247-01 | 24/7 availability monitoring | Continuous | SLO dashboard | Customer service |
| C-FPS-SCAM-01 | APP fraud (authorised push payment) detection | Per tx | Fraud log | Customer protection |

## APP fraud note

UK has dedicated reimbursement scheme for APP scam victims (post-Oct 2024 PSR mandate). Payer + payee PSPs share liability 50/50. Drives heavy investment in pre-payment scam scoring + post-payment investigation.

## Linked

[[sct-inst-control-catalog]] · [[../concepts/fps]] · [[../concepts/cop]]
