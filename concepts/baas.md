# BaaS — Banking as a Service

Bank rents regulated charter + infrastructure to fintech / brand for embedded financial products.

## Stack

```
End user
   ↓
Brand / Fintech UI
   ↓
BaaS provider (orchestration layer, often middleware)
   ↓
Sponsor Bank (regulated entity, balance sheet, license)
```

## Examples

- **Sponsor banks**: Solaris (DE), Treezor (FR), Railsr (UK, post-restructure), Synapse (US, collapsed 2024), Cross River (US), Stripe Issuing partners, BBVA, Goldman
- **Middleware**: Unit, Rapyd, Bond (acquired by FIS)
- **End brands**: any non-bank wanting accounts / cards / payments

## Bank's perspective

- Rev: per-account or per-tx fees + FX margin + interchange share
- Cost: tech integration, ongoing AML / risk monitoring
- Risk: reputational + regulatory if fintech mishandles

## Risks (post-2024 stress)

- Synapse collapse 2024 demonstrated weak segregation between brand customer money + middleware ops
- US OCC enforcement against several BaaS sponsor banks 2024-25
- EU regulators cautioning on BaaS oversight (BaFin actions vs Solaris)
- Customer ledger separation + reconciliation discipline now critical

## Cash mgmt link

- BaaS sponsor bank's treasury manages all underlying flows
- Aggregated multi-tenant operating accounts
- Customer money segregation per safeguarding rules ([[../regulations/psd2-psd3]] art 10)

## Related

[[embedded-finance]] · [[bin-sponsorship]] · [[../decisions/0011-baas-vs-direct]]
