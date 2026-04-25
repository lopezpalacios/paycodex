# NFR — Compliance + data

## Data sovereignty

- EU data: store in EU (default Frankfurt / Dublin / Amsterdam zones)
- CH data: prefer CH-resident processing where possible
- UK data: post-Brexit adequacy decision currently in place
- Cross-border: EU-CH adequacy; EU-US Data Privacy Framework

## Retention

| Data type | Retention | Driver |
|---|---|---|
| Payment transactions | 10y | CH/EU banking law |
| KYC / AML evidence | 10y post-relationship | AMLD / AMLA |
| Mandate documents | Life + 14m post-last-use | EPC SDD scheme |
| Audit logs | 10y | Banking law |
| Customer comms | 10y | MiFID II for advised |
| Marketing consent | Until withdrawn | GDPR |

## Crypto + key management

- Per legal entity: separate KMS hierarchy (segregation)
- Customer master keys held in HSM (FIPS 140-2 Level 3+)
- Application keys derived, rotated 90d
- Key escrow for legal disclosure obligations

## Right to erasure (GDPR Art 17)

- Tension with banking retention obligations
- Solution: erasure deferred until retention period ends
- Public-facing display masked sooner where appropriate

## Linked

[[security]] · [[../regulations/gdpr]] · [[../regulations/fadp]]
