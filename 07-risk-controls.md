# 07 — Risk & Controls (CH + EU + UK)

Stop fraud, meet regulation, survive cyber.

## Entitlements

- Role-based: initiator, approver, admin
- Limits: per-transaction, per-day, per-account
- Dual approval (maker/checker) above threshold
- IP whitelisting, geo-fencing, device binding
- PSD2 SCA + dynamic linking for online channels
- Defined in [[01-onboarding]] resolutions

## Payee verification

- [[concepts/vop]] — EU SEPA-wide, mandatory Oct 2025 under IPR
- [[concepts/cop]] — UK, live since 2020
- Forces IBAN/name match before send
- Liability shifts on override

## Direct Debit fraud / mandate controls

- [[concepts/sepa-sdd]] — Core has 8-week unconditional refund, B2B has none
- Mandate verification + UMR uniqueness ([[concepts/sepa-mandate]])
- Bacs Direct Debit Guarantee — UK consumer indemnity, creditor-funded
- [[concepts/positive-pay]] — for residual cheque flows (mostly UK / FR)

## Wire / payment fraud

- BEC (business email compromise) = top loss vector
- Callback verification on new beneficiaries
- Behavioral analytics — velocity, amount, geography
- AI/ML scoring on high-value [[concepts/wire]] traffic + instant rails

## Sanctions / AML

- [[concepts/ofac]] + EU consolidated list + SECO (CH) + UK OFSI screening every payment
- 50% rule applied (US OFAC + EU)
- Hit handling: block / reject / SAR
- Foundation in [[concepts/kyc-aml]] during [[01-onboarding]]
- IPR shifts instant payments to **daily customer screening** vs per-transaction

## Operational resilience

- [[regulations/dora]] in force Jan 2025 — major incident reporting, TLPT, third-party register
- SWIFT CSP mandatory controls
- API security: OAuth2, mTLS, rate limiting, JWT
- SOC 2 Type II, ISO 27001 expected

## Data protection

- [[regulations/gdpr]] (EU/UK) + [[regulations/fadp]] (CH)
- DPIA on fraud monitoring + behavioral analytics
- Cross-border transfer safeguards

## Cross-links

Wired into [[03-tech-integration]] auth layer. Operated by service team in [[04-daily-ops]]. Fraud loss hits P&L tracked by [[05-relationships]] RM.

← [[README]]
