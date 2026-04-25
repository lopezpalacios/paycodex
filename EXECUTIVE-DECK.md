---
marp: true
theme: default
paginate: true
backgroundColor: #fff
header: 'Cash Management Knowledge Graphs'
footer: '© 2026 — open-source · MIT'
style: |
  section {
    font-size: 22px;
  }
  h1 { color: #1a3a6e; }
  h2 { color: #1a3a6e; }
  table { font-size: 18px; }
  code { background: #f0f0f0; padding: 2px 4px; }
---

# Cash Management Knowledge Graphs

**Incumbent Rails + DLT/EVM**
Two cross-linked open-source documentation graphs

Executive briefing
2026

---

## The problem we solved

- Cash management spans **3 currencies, 16 rails, 21 regulations, 100s of vendors**
- Knowledge fragmented across treasury sales, compliance, engineering, ops
- New hires take **months** to ramp; architecture decisions take **weeks**
- DLT is parallel stack — same products, different tech
- Strategic decisions need **cross-domain synthesis** that doesn't exist in any single doc

**Result: slow decisions, repeated mistakes, vendor lock-in by accident**

---

## What we built

Two cross-linked Obsidian-style knowledge graphs.

**Graph 1 — `cashmgmt/`** (incumbent CH/EU/UK rails)
- 314 markdown files
- 16 vertical implementation slices
- Full process / state / data / architecture / controls / runbooks / ADRs

**Graph 2 — `cashmgmt-dlt/`** (parallel EVM-based DLT)
- 161 files (137 markdown + 24 Solidity)
- Top 100 use cases ranked easy → hard
- All cross-linked to Graph 1

**Total: 475 files. Stack-agnostic logical models + vendor-specific physical mappings.**

---

## Coverage map (incumbent)

| Domain | Coverage |
|---|---|
| **CH rails** | SIC, SIC IP, euroSIC, QR-bill, eBill, TWINT, PostFinance |
| **EUR rails** | SCT, SCT Inst, SDD Core/B2B, T2, TIPS, STEP2, RT1 |
| **GBP rails** | CHAPS, Bacs, FPS, CoP |
| **Cross-border** | SWIFT/gpi, MT↔MX, correspondent chain |
| **Securities** | T2S DvP, CSDR, corp actions cash |
| **CBDC** | Wholesale (Helvetia), retail (digital euro) |
| **Adjacent** | Cards, trade finance, BaaS, FX hedging, ESG, Open Banking |
| **Regulations** | PSD2/3, IPR, WTR, AMLA, DORA, GDPR, MiCA, Basel III, MiFID II, EMIR + 11 more |

---

## Coverage map (DLT/EVM parallel)

| Domain | Coverage |
|---|---|
| **Chains** | Ethereum L1, Base, Arbitrum, Optimism, zkSync, Polygon (PoS + zkEVM), Linea + Besu, Quorum, Canton EVM (permissioned) |
| **Cash legs** | Stablecoin (USDC/EURC), tokenized deposit (JPMD/EURCV/DCHF), wholesale CBDC (Helvetia), retail CBDC (digital euro), tokenized MMF (BUIDL) |
| **ERC standards** | ERC-20, 721, 1155, 1400, 3643 (T-REX), 4626, 4337 (AA), 2535 (Diamond), 2612 (permit), 7281 (xERC20) |
| **Compliance** | Travel Rule SDKs, T-REX permissioned, MiCA, FINMA DLT Act, EU DLT Pilot |
| **Custody** | MPC (Fireblocks), HSM (Thales), Gnosis Safe |

---

## Business value — by persona

| Persona | Pain today | What graph delivers |
|---|---|---|
| **Treasury sales** | Generic pitches lacking depth | Ready answers per rail with comparison matrices |
| **Solution architect** | Reinventing every project | Reusable patterns + ADRs + vendor maps |
| **Engineering lead** | Slow ramp, unclear contracts | Stack-agnostic data models + state machines + Solidity snippets |
| **Compliance officer** | Audit prep from scratch | Control catalogs mapped to regulations + deadline tracker |
| **Ops** | Tribal knowledge incident response | Runbooks for top exception scenarios |
| **Strategy** | Vendor / build / partner without data | Build-vs-buy matrix per component, ADRs |

---

## Time-to-value examples

**Onboarding a new payments engineer**
- Before: 3 months to productive contribution
- With graph: 3 weeks (start at sector → process → entity → snippet)

**RFP response for corporate cash mgmt mandate**
- Before: 4 weeks of cross-team interviews
- With graph: 1 week — pull from coverage matrices + ADRs

**DORA / IPR / CSRD compliance audit prep**
- Before: 2 quarters of evidence collection
- With graph: 1 quarter — control catalogs already mapped to regs

**Architecture review board**
- Before: discussions stuck on "what's our pattern for X?"
- With graph: ADR exists or doesn't; if not, write one in 1h template

---

## What makes it different from Confluence/Notion

- **Atomic concept notes** — each idea has its own file, ~50-200 lines
- **Cross-links as first-class** — Obsidian wikilinks `[[note-name]]`, graph view exposes relationships
- **Stack-agnostic logical layer + vendor-specific physical layer** — separated cleanly
- **Mermaid diagrams + Solidity snippets inline** — runnable, not just descriptive
- **Implementation-ready** — entity schemas, state machines, control catalogs, all live in repo
- **Versioned via git** — diff-able, branchable, reviewable like code

→ Treat documentation as code.

---

## DLT/EVM parallel — same products, different tech

**Incumbent SCT Inst (EUR instant)**
- 24/7 (post-IPR Oct 2025), <10s, scheme cap, VOP mandatory
- Settlement via TIPS/RT1
- Cost: €0.05-€0.30

**EVM equivalent — ERC-20 transfer (e.g., USDC/EURC)**
- 24/7 always, ~12s on L1, ~1s on L2
- Settlement on chain
- Cost: $0.001-$5 (chain-dependent)
- **Adds**: 24/7 native, programmable, atomic, composable
- **Trade-offs**: privacy, regulatory clarity (improving), key management

→ Strategic question is **not** "DLT or incumbent" — it's **"which product on which rail"**.

---

## The four+1 cash legs (executive must-know)

| Type | Issuer | Tier of money | Use case |
|---|---|---|---|
| **Stablecoin (public)** | Private EMI | Tier 2 | DeFi treasury, FX, cross-border |
| **Tokenized deposit** | Licensed bank | Tier 2 | Interbank deposits, in-house bank |
| **Wholesale CBDC** | Central bank | **Tier 1** | DvP wholesale, interbank |
| **Retail CBDC** | Central bank | **Tier 1** | Retail consumer (when live) |
| **Tokenized MMF** | Asset manager | Investment | Idle cash yield |

→ Different legal status, regulatory framework, settlement model.
→ A "stablecoin strategy" without this distinction = strategic error.

---

## Top 100 use cases — easy → hard

**Tier 1 (easiest)**
- ERC-20 instant transfer · transfer with structured ref · batch payroll · sanctions blocklist on-chain

**Tier 2 (moderate)**
- Atomic FX swap · Direct debit smart contract · Sweep keeper · Tokenized MMF (ERC-4626)

**Tier 3 (intermediate)**
- DvP atomic settlement · Tri-party repo · Letter of credit · Invoice tokenization

**Tier 4-5 (advanced)**
- Cross-chain DvP · ESG-linked loan with KPI oracle · Multi-bank syndicated loan · Travel Rule on-chain

**Tier 6 (frontier)**
- Confidential transfer (Aztec) · ZK-KYC · Diamond tokenization platform

→ 24 use cases have **runnable Solidity demos** in Foundry.

---

## How to use it — 5 paths

1. **Concept-first** — open any atom, follow `[[wikilinks]]` to related concepts
2. **Process-first** — open process → state machine → entity → controls → runbook
3. **Implementation-first** — pick architecture pattern → entity → controls → snippet
4. **Audit-first** — control catalog → traces to regulations → evidence list
5. **Compliance-first** — deadline tracker → priority projects per quarter

**Tools that work**: Obsidian (recommended) · VSCode (with Foam extension) · GitHub web · Logseq · plain text

---

## Strategic positioning

**Internal use cases**
- Architecture review board reference
- Engineering onboarding curriculum
- Compliance audit evidence collection
- Vendor RFP response source

**External use cases**
- Customer pitch material (cash management capabilities)
- Industry thought leadership (open-source contribution)
- Talent attraction (engineers see depth + clarity)
- Standard-setting participation (publish reference patterns)

**RAG / AI use cases**
- Embed graph as corpus for AI assistants
- Custom GPTs trained on our cash mgmt domain
- Internal AI-powered docs search

---

## Roadmap

**Now** — graphs covering CH/EU/UK incumbent + EVM-DLT parallel

**Q3 2026**
- Quarterly regulatory deadline refresh ([[regulations/deadline-tracker]])
- Vendor profile updates (post-2024 BaaS shakeout, new entrants)
- Additional Solidity snippets (top 100 → top 30 with code)

**Q4 2026**
- Open contribution model (PRs welcome from industry peers)
- RAG-ready embeddings published
- Community engagement at industry conferences

**2027+**
- Asia-Pacific incumbent rails (Hong Kong, Singapore, India)
- Latin America (Pix, real-time pay corridors)
- Tokenized bond issuance live use cases
- Digital euro post go-live updates

---

## Call to action

**For executives**
- Read [[03-cash-legs-comparison]] — strategic frame, 5 minutes
- Review [[regulations/deadline-tracker]] — mandates next 24 months
- Prioritize 1-2 vertical slices for organization to internalize

**For architecture**
- Adopt [[architecture/]] patterns as starting points
- Add ADRs in [[decisions/]] for big choices
- Plug into vendor selection process

**For engineering**
- Run a Solidity snippet from [[code/]] in 30 minutes
- Apply state machine + entity model to next product build
- Contribute back missing patterns

---

## Open source — repos

**`paycodex`** — incumbent rails (CH/EU/UK)
GitHub: `github.com/lopezpalacios/paycodex`

**`paycodex-onchain`** — DLT/EVM parallel
GitHub: `github.com/lopezpalacios/paycodex-onchain`

**License**: MIT (code) + CC-BY-SA-4.0 (docs)

**Contributions welcomed** — PRs for:
- Regulatory updates (new deadlines, scheme rule changes)
- New rails (international expansion)
- New ERC standards
- Vendor profile updates
- Solidity snippet additions

---

## Thank you

Questions? Open the graph and explore.

`cd ~/projects/cashmgmt && obsidian .`
`cd ~/projects/cashmgmt-dlt && obsidian .`

