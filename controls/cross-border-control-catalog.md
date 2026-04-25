# Cross-border wire — control catalog

| ID | Control | Frequency | Evidence | Risk | Reg |
|---|---|---|---|---|---|
| C-XB-SAN-01 | Per-tx full sanctions screening (incl free-text :70/RmtInf) | Per transaction | Engine log | Sanctions breach | [[../regulations/wtr-travel-rule]] |
| C-XB-WTR-01 | Travel rule data completeness | Per transaction | Pre-send validation | Reg breach | [[../regulations/wtr-travel-rule]] |
| C-XB-CBPR-01 | CBPR+ structured address mandatory (post Nov 2025) | Per transaction | Validation log | Bank rejection downstream | SWIFT scheme |
| C-XB-FX-01 | FX rate disclosure to originator | Per FX leg | Quote artifact | Conduct (PSD2 transparency) | [[../regulations/psd2-psd3]] |
| C-XB-CHG-01 | Charge bearer disclosure (OUR/BEN/SHA fees) | Per quote | Pre-send disclosure | Conduct | PSD2 |
| C-XB-NST-01 | Nostro position monitoring | Real-time | Position dashboard | Liquidity | Bank policy |
| C-XB-NST-02 | Nostro reconciliation T+1 | Daily | Recon report | Loss of cash visibility | Bank policy |
| C-XB-CSP-01 | SWIFT CSP annual attestation | Annual | Attestation submission | SWIFT scheme | SWIFT mandatory |
| C-XB-GPI-01 | gpi tracker status update posting | Per leg | Tracker query | gpi commitment | SWIFT gpi |
| C-XB-INV-01 | Investigation response SLA | Per case | Case mgmt log | Customer commitment | Bank policy |
| C-XB-REP-01 | Recall request handling (camt.056) | Per request | Case + outcome | Customer commitment | EPC + scheme |
| C-XB-AML-01 | Cross-border AML enhanced monitoring | Continuous | TM rules + alerts | Reg breach | [[../regulations/amld-amlr-amla]] |

## Test approach

- Unit: address validation, charge bearer fee math, UETR generation
- Integration: SWIFT test environment for full message flow
- E2E: end-to-end test wires through sandbox correspondent chain
- Performance: high-value batch (e.g., 10K MT103 / pacs.008 in window)
- Negative: malformed structured address, invalid BIC, sanctions hit

## Linked

[[sct-inst-control-catalog]] · [[../regulations/wtr-travel-rule]]
