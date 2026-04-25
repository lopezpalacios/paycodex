# RACI — SCT Inst delivery

**R**=Responsible · **A**=Accountable · **C**=Consulted · **I**=Informed

## Build phase

| Activity | Treasury Sales | Implementation TMO | Tech / Eng | Compliance | Risk | Ops | Audit |
|---|---|---|---|---|---|---|---|
| RFP response | A/R | C | C | I | I | I | I |
| Onboarding | C | A/R | C | C | C | I | I |
| Tech integration | I | C | A/R | I | I | I | I |
| Sanctions integration | I | C | R | A | C | I | C |
| VOP integration | I | C | R | A | C | I | C |
| UAT | C | A/R | R | C | C | C | I |
| Go-live signoff | C | A/R | C | C | C | C | I |

## Run phase

| Activity | TSO | TMO | Tech | Compliance | Risk | Ops | Audit |
|---|---|---|---|---|---|---|---|
| Daily ops | I | I | I | I | I | A/R | I |
| Sanctions hit handling | I | I | C | A | C | R | I |
| Fraud alert handling | I | I | C | C | A | R | I |
| Major incident | I | C | R | I | A | R | I |
| Annual control testing | I | I | C | C | A | C | R |

## Notes

- Compliance is **A** for any sanctions-touching decision
- Risk is **A** for fraud + operational risk
- Ops own **R** for run-the-bank activities
- Audit **R** for control testing (independent third line)

## Linked

[[../05-relationships]] · [[sct-inst-control-catalog]]
