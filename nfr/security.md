# NFR — Security

Auth, crypto, network, data classification.

## Authentication

- **Customer**: PSD2 SCA (3DS2, dynamic linking, behavioral biometrics)
- **Internal users**: SSO + MFA (FIDO2 keys preferred)
- **Service-to-service**: mTLS + OIDC tokens
- **API customers**: OAuth2 client-credentials + mTLS

## Authorization

- Role-based (initiator, approver, admin)
- ABAC for fine-grained (entitlements per customer + amount)
- Dual approval over thresholds

## Crypto

- TLS 1.3 minimum on all transport
- Data at rest: AES-256-GCM, KMS-managed keys (per legal entity)
- Crypto-agility: HSM + named-key abstractions (rotation friendly)
- Quantum-readiness: track NIST PQC standardization, plan migration

## Network

- Zero-trust internal: no implicit trust between services
- Segmentation per data classification
- Egress allowlists for vendor APIs
- DDoS protection at edge

## Data classification

| Tier | Examples | Controls |
|---|---|---|
| Public | Marketing pages | Standard |
| Internal | Org charts, runbooks | Auth required |
| Confidential | Customer data, payment data | Encryption + DLP |
| Restricted | Sanctions data, fraud models | Need-to-know + audit |

## Compliance

- SOC 2 Type II
- ISO 27001
- PCI DSS if card-touching
- SWIFT CSP (if SWIFT participant)

## Linked

[[../regulations/dora]] · [[../regulations/gdpr]] · [[compliance-data]]
