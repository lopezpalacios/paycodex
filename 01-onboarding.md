# 01 — Onboarding (CH + EU + UK)

How bank brings corporate client live on cash management.

## KYC/AML

- Beneficial ownership ≥25% — Swiss [[regulations/swiss-amla]] Form A; EU [[regulations/amld-amlr-amla]]
- Entity docs: trade register extract (HR / Handelsregister CH; Companies House UK; equivalent EU national registers), articles, EID, signatory mandates
- Sanctions screening: [[concepts/ofac]] + EU consolidated list + SECO (CH) + UK OFSI
- Risk rating: low/medium/high based on industry (MSB, crypto, cannabis = high), geography, ownership
- Enhanced due diligence (EDD) for high-risk: source of wealth + funds, site visits
- Full process detail: [[concepts/kyc-aml]]

## Credit review

- Even non-credit cash mgmt needs credit line for daylight overdraft, [[concepts/sepa-sdd]] return exposure, FX settlement
- Daylight OD limit = max intraday negative balance bank tolerates
- SDD credit risk = bank funds creditor before debtor settlement (refund risk via Direct Debit Guarantee in UK / SDD Core refund right)

## Legal docs

- Master Treasury Services Agreement (umbrella)
- Service-specific schedules ([[concepts/sepa-sdd]] mandate management, [[concepts/wire]], [[concepts/sct-inst]])
- Account resolutions — board authorizes signatories / initiators
- Governing law: Swiss CO + AGB (CH); EU member-state law per branch; English law (UK)

## RFP process

- Big corp issues 50-200 page RFP, banks bid
- Scored on: pricing ([[06-pricing-revenue]]), tech ([[03-tech-integration]]), geography, credit appetite, service team ([[05-relationships]])
- Implementation timeline 3-12 months for global mandate

## Outputs

- Client live on portal + entitlements ([[07-risk-controls]])
- Account structure opened ([[02-products]])
- Tech rails connected ([[03-tech-integration]])

← [[README]]
