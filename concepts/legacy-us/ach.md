# ACH — Automated Clearing House

US batch electronic payment rail. Operated by The Clearing House and Federal Reserve. Governed by NACHA rules.

## Flow

1. Originator (ODFI bank) submits NACHA file
2. ACH operator routes to receiving bank (RDFI)
3. Settlement next day (standard) or same day (3 windows)

## Same-day windows (ET)

- 10:30am, 2:45pm, 4:45pm

## Credit vs debit

- Credit = push (payroll, vendor pay)
- Debit = pull (bill pay, subscription, B2B collection)
- Debit creates fraud / authorization risk → ACH controls in [[07-risk-controls]]

## Return codes

R01 NSF · R03 no account · R10 unauthorized · R29 corp not authorized

## Related

[[wire]] · [[rtp-fednow]] · [[03-tech-integration]] · [[04-daily-ops]]
