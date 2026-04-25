# Control: Real-time fraud ML scoring

**ID**: C-FRD-01

## Description

Each outbound (and high-risk inbound) payment scored by ML model in <200ms. Score + decision logged. Threshold hits route to step-up or block.

## Inputs

- Payment fields (amount, currency, beneficiary, counterparty history)
- Customer behavioral features (typical amount, geography, time of day)
- Device + session features (PSD2 SCA telemetry)
- Beneficiary risk signals (new beneficiary, recently added)
- Network features (graph-based — if customer's contacts had fraud)

## Decisions

- Pass: score below threshold → proceed
- Step-up: medium score → additional auth
- Block: high score → hold for review

## Threshold management

- Tuned per channel + per rail
- Continuous A/B + drift monitoring
- Quarterly model refresh

## Evidence

- Score + model version per payment
- Override decisions logged
- Confusion matrix tracking (false positive / false negative)
- DPIA per [[../regulations/gdpr]] (profiling)

## Linked

[[../regulations/psd2-psd3]] · [[../07-risk-controls]]
