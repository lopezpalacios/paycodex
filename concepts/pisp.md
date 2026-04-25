# PISP — Payment Initiation Service Provider

PSD2-regulated entity that initiates payments from customer's bank account on customer's behalf.

## What PISP can do

- Initiate single immediate payment ([[../concepts/sct-inst]] / [[../concepts/fps]])
- Initiate scheduled payments
- Some markets: bulk payments
- Cannot hold customer funds

## Examples

- Trustly (open banking payments)
- TrueLayer Payments
- Token.io
- Volt
- Pay.UK Variable Recurring Payments (VRP) — extends PISP for recurring

## Use case

- E-commerce checkout (cheaper alternative to cards — no interchange)
- B2B initiated payments
- Bill pay

## Liability

- PISP doesn't take settlement risk (bank executes)
- PISP responsible for proper customer authentication
- Bank not liable for PISP's misbehavior beyond statutory consumer protection

## Related

[[aisp]] · [[../regulations/psd2-psd3]] · [[../concepts/sct-inst]] · [[../concepts/fps]]
