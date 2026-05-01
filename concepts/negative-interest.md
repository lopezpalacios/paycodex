# Negative interest

Rate environment where the policy rate is below zero. Bank's deposit at central bank earns NEGATIVE return; passes through (selectively) to customers.

## Where it happened (and where it might again)

| Central bank | Negative-rate period | Floor reached | Mechanism |
|---|---|---|---|
| ECB (EUR) | Jun 2014 – Jul 2022 | −0.50% (DFR) | Two-tier reserve exemption (later) |
| SNB (CHF) | Jan 2015 – Sep 2022 | −0.75% | Tier exemption (25× reserve req) |
| BoJ (JPY) | Jan 2016 – Mar 2024 | −0.10% | Three-tier system |
| Riksbank (SEK) | Feb 2015 – Dec 2019 | −0.50% | Single-rate |
| Nationalbanken (DKK) | Jul 2012 – Mar 2022 | −0.60% | Penalty rate |

ECB and SNB are the case studies most relevant to CH/EU corporates.

## Two-tier exemption (ECB and SNB)

To soften pass-through, central banks excluded a portion of bank reserves from the negative rate:

**SNB:** Each bank's "exemption threshold" = 25× minimum reserve req. Reserves up to threshold earn 0%, above earn negative.
**ECB:** Tier 1 (6× minimum reserve) at 0%; Tier 2 (above) at the (negative) deposit facility rate. Introduced Oct 2019.

Exemption thresholds were political concessions — protected most of the banking system from full pass-through pain.

## Customer pass-through patterns

| Customer | Pass-through |
|---|---|
| Retail | Almost never (run risk, political) |
| SME | Below CHF/EUR 250k–500k usually exempt |
| Corporate | Above threshold (typ. CHF/EUR 250k–10m) charged the negative rate |
| Financial institutions | Full pass-through |
| Public sector | Often exempt by political decision |

Banks priced as "deposit fee" or "balance maintenance fee" (semantic — same effect as negative interest).

## Floor mechanics

Most retail and many SME deposit products have a hard 0% floor. Effectively the floor in [[interest-calculation]]:

```
effective rate = max(policy + spread, floor)
```

See `paycodex-rules-poc/rules/examples/06-floor-cap.json` for the rule expression.

## On-chain modelling

`FloatingStrategy` contract supports `floorBps` parameter. Setting `floorBps=0` blocks negative pass-through to depositor. See [[../../paycodex-onchain/code/XX-floor-cap-deposit.sol]].

## Why it matters now (2026)

After 2022 normalisation, policy rates have moved up but central banks reserve the option to return to negative if recession + low inflation re-emerges. Deposit products built TODAY should support negative-rate operation as a configuration, not a code change.

## Related

[[interest-calculation]] · [[deposit-pricing]] · [[reference-rates]] · [[../operators/snb]] · [[../operators/ecb]]
