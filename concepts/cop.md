# Confirmation of Payee (CoP)

UK IBAN-equivalent / sort-code+account name match check. Live since 2020.

## How it works

- Payer enters sort code + account number + name
- Sending PSP queries receiving PSP via API
- Response: match / close match / no match / not in scheme
- Liability shifts on no-match override

## Coverage

- Phase 1 (2020): top 6 banks
- Phase 2 (2023): all PSPs holding consumer accounts
- Now broadly mandatory for credit transfers in UK

## Predecessor / model for [[vop]]

EU IPR's VOP design heavily inspired by CoP UK rollout. Same shape, pan-SEPA scope.

## Tech

- API standard via Pay.UK
- Performance critical — sits in payment journey UX
- Trusted vendors: Surepay, Mastercard / Vocalink

## Related

[[vop]] · [[fps]] · [[chaps]] · [[../operators/pay-uk]]
