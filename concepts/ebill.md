# eBill — Swiss e-invoicing

Swiss e-invoicing network operated by SIX. Bank-channel-native — not a third-party invoicing vendor.

## Flow

1. Biller registers with eBill via their bank
2. Customer opts in via e-banking portal ("activate eBill from biller X")
3. Biller pushes invoice → eBill network → customer's e-banking inbox
4. Customer approves → payment auto-initiated via SIC
5. Confirmation back to biller

## Why Swiss-specific

- Bank consortium product, no equivalent in EU/UK at same scale
- Tight integration with [[qr-bill]] data model
- Replaces paper invoice + QR-bill payment for users opted in

## B2B / B2C

- Both. B2B uses invoice approval workflows
- B2C uses simple opt-in / approve / pay

## Tech

- ISO 20022 invoice messages
- API for biller integration
- Consumer interface lives in each bank's e-banking app

## Related

[[qr-bill]] · [[twint]] · [[../02-products]]
