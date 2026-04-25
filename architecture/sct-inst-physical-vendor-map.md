# SCT Inst — physical / vendor mapping

Same logical components ([[sct-inst-logical]]) — multiple realizations.

## Component-by-component options

| Component | Build | Vendor options |
|---|---|---|
| Payment Hub | Kotlin/Java + Postgres + Kafka | Volante VolPay · Form3 · Finastra Global PAYplus · ACI Worldwide · FIS Open Payment Framework |
| CSM Adapter | Custom TIPS / RT1 client | Same hub vendors usually include |
| VOP Service | OpenAPI client + cache | SurePay (NL) · iPiD · EBA Fraud Pattern Detection |
| Sanctions Screening | n/a | Fircosoft (Accuity) · LexisNexis Bridger · Refinitiv WorldCheck · ComplyAdvantage · NICE Actimize |
| Fraud Engine | n/a (need ML platform) | Featurespace · Hawk AI · NICE Actimize · BAE Systems NetReveal · ThetaRay |
| Customer Master | Custom + standard CRM | Salesforce / Microsoft Dataverse · Pega CLM |
| Account / Ledger | Custom or core banking | Thought Machine · Mambu · 10x · Temenos T24 · Avaloq · Finacle · core banking |
| Liquidity | Custom | Often hub-bundled or in-house |
| Event Bus | n/a | Kafka · Confluent Cloud · AWS MSK · Solace · RabbitMQ · Pulsar |
| Channel Gateway | Custom | Bottomline · Volante · API Gateway products |
| SWIFT Gateway | n/a | SWIFT Alliance Access / Lite2 · Bottomline SWIFT Service Bureau |

## Build vs Buy decision factors

| Factor | Build | Buy |
|---|---|---|
| Time to market | 18-36 months | 6-12 months |
| Differentiation | High | Low |
| TCO 5y | Lower if reused | Lower if niche |
| Talent | Hard to retain | Vendor SLA |
| Regulatory change agility | High | Vendor-dependent |
| Multi-rail reuse | High if abstracted | Vendor scope |

## Hybrid pattern (most common)

- Buy: Hub + CSM adapter (regulated complexity)
- Buy: Sanctions screening + fraud (data + models)
- Build: Orchestration, integrations, customer-facing
- Build or Buy: VOP (most banks buy)

## Per-bank archetypes

- **Big universal** (UBS, JPM, BNP) — heavy build + selective vendors, multi-rail
- **Mid-tier / cantonal** — vendor-heavy, payment hub from one vendor
- **Challenger / neobank** — modern stack, Form3 / 10x / Mambu, cloud-native
- **Custodian / wholesale only** — rail subset, minimal retail tech

## Linked

[[sct-inst-logical]] · [[../decisions/0002-vendor-payment-hub]]
