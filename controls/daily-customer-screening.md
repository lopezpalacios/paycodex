# Control: Daily customer screening

**ID**: C-SAN-01

## Description

All customers (PSP account holders) screened against sanctions lists daily and on list update events. Result determines whether their payments can flow without additional per-tx review.

## Why daily, not per-transaction

- Instant payments (10s SLA) cannot afford full per-tx fuzzy screening
- IPR Art. 5d explicitly accepts this approach
- Shifts compliance from runtime to batch

## Trigger

- Nightly scheduled run
- Sanctions list update event (real-time delta processing)
- Customer creation / update event (synchronous re-screen)

## Implementation

- See [[../architecture/sanctions-cache-pattern]]
- See [[../processes/sanctions-screening-flow]]

## Lists

- OFAC SDN + sectoral
- EU consolidated list
- SECO (CH)
- UK OFSI
- UN sanctions
- Internal watchlists

## Evidence

- Run log: timestamp, list versions, customer count, hits, runtime
- Hit handling decisions: alert, escalation, blocking action
- List version inventory + last-loaded timestamps

## Test cases

- Known SDN match in test data → blocked
- 50% rule entity → blocked
- Fuzzy match (similar name) → flagged for review
- List update mid-day → delta re-screened
- Customer onboarded mid-day → synchronous screen before activation

## Reg mapping

- [[../regulations/instant-payments-regulation]] Art. 5d
- [[../regulations/wtr-travel-rule]]
- [[../regulations/amld-amlr-amla]]

## Linked

[[../concepts/ofac]] · [[../runbooks/sanctions-hit-handling]]
