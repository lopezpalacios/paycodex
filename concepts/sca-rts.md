# SCA RTS — Strong Customer Authentication Regulatory Technical Standards

EU Reg 2018/389. Detailed rules for SCA + secure communication under PSD2.

## SCA elements

Two of three required:

- **Knowledge** (something user knows: PIN, password, secret)
- **Possession** (something user has: phone, hardware token, app)
- **Inherence** (something user is: fingerprint, face, behavior)

## When required

- Online payments
- Account login (with frequency limit)
- Initiating payment (each one or per session)
- Some exemptions: low-value, recurring, trusted beneficiary, corporate payment

## Dynamic linking

For payment SCA, auth code must bind to:

- Specific amount
- Specific payee
- One-time use

Catches MITM attacks that swap beneficiary.

## Secure Open Communication

- Dedicated PSP API (preferred)
- Or "modified customer interface" fallback (banks must avoid blocking TPPs)
- mTLS + qualified certificates (eIDAS)

## PSD3 changes

- Killing "modified customer interface" fallback
- Tighter API quality + uptime requirements
- Stronger TPP fairness rules

## Related

[[aisp]] · [[pisp]] · [[../regulations/psd2-psd3]] · [[../07-risk-controls]]
