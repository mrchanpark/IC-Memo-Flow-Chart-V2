# IC Memo Production Workflow — LLM Capability Map

### Generalized Investment Committee Memo — Blueprint v3.1

> **184 actionable steps** · **7 stages** · **5 validation gates** · **1 decision-rights freeze** · **19 content sections**
> Asset-class agnostic: venture, growth equity, PE, credit, real assets.
> Every step classified by what an LLM can and cannot do.
> v3.1 adds: process controls, sign-off semantics, change control, assumption governance, valuation method applicability.

---

## LLM Capability Legend

| Color | Meaning | Description |
|:---:|---|---|
| 🔴 | **LLM Cannot Do** | Requires human judgment, proprietary data access, legal authority, or physical sign-off |
| 🟡 | **LLM Needs Human Assistance** | LLM can draft/compute but needs human to supply data, validate, or approve output |
| 🟢 | **LLM Can Do** | LLM can execute independently given prior context and data from earlier steps |

## Sign-Off Types (New in v3.1)

| Type | Meaning | Who |
|---|---|---|
| **ATTESTATION** | Domain data is accurate and reconciled | Finance, Legal, Commercial owners |
| **CERTIFICATION** | Memo is production-ready, consistent, all gates passed | Memo Owner |
| **APPROVAL** | Investment recommendation, terms, and strategy endorsed | Deal Sponsor |
| **PREREQUISITE** | Governance/policy requirement fulfilled | Board Chair, External Counsel |

---

## Pre-Production: Transaction Intake

> *Mostly 🔴 — these are Deal Sponsor decisions that set every downstream parameter.*

```mermaid
flowchart LR
  P01(["Deal Sponsor: Initiate memo production"]):::red --> P02["Define transaction type & asset class"]:::red
  P02 --> P03["Set transaction size & structure"]:::red
  P03 --> P04["Establish valuation basis"]:::yel
  P04 --> P05["Document IC decision required"]:::yel
  P05 --> P06["Set confidentiality tier"]:::red
  P06 --> P07["Lock data cutoff date"]:::red
  P07 --> P08["Set draft & final timeline"]:::yel
  classDef red fill:#fecaca,stroke:#dc2626,color:#7f1d1d
  classDef yel fill:#fef3c7,stroke:#d97706,color:#78350f
```

## Pre-Production: Ownership & Scoping Decisions

> *Mostly 🔴 — personnel assignments and deal structure decisions are human-only. v3.1: Memo Owner is the single accountable owner; version control established at scoping.*

```mermaid
flowchart TB
  P09["Assign Memo Owner (single accountable)"]:::red --> P10["Assign Financial Data Owner"]:::red
  P10 --> P11["Assign Legal / Capital Structure Owner"]:::red
  P11 --> P12["Assign Commercial / Operating Owner"]:::red
  P12 --> P13["Resolve scoping with Deal Sponsor"]:::red
  P13 --> P14{"Co-invest / secondary?"}:::redD
  P14 -- Yes --> P15["Document co-investors & allocation"]:::red
  P14 -- No --> P16{"Existing investor participation?"}:::redD
  P15 --> P16
  P16 -- Yes --> P17["Document follow-on commitments"]:::red
  P16 -- No --> P18["Confirm syndication strategy"]:::red
  P17 --> P18
  P18 --> P19["Finalize page budget"]:::yel
  P19 --> P20["Establish memo version control"]:::yel
  classDef red fill:#fecaca,stroke:#dc2626,color:#7f1d1d
  classDef redD fill:#f87171,stroke:#dc2626,color:#7f1d1d,font-weight:700
  classDef yel fill:#fef3c7,stroke:#d97706,color:#78350f
```

---

## 🚧 Gate 1: Key Metric Definitions & Measurement Policy Lock

> *🟡 LLM can propose standard definitions, but Finance must confirm methodology. v3.1: Renamed for asset-class neutrality; includes metric framework selection by asset class.*

```mermaid
flowchart LR
  A["Define revenue recognition methodology"]:::yel --> B["Define retention / renewal rate calc"]:::yel
  B --> C["Define attrition: customer vs. revenue"]:::yel
  C --> D["Define origination cost scope"]:::yel
  D --> X["Select asset-class metric framework"]:::yel
  X --> E{"All definitions locked?"}:::redD
  E -- No --> A
  E -- Yes --> F["Finance Owner: ATTESTATION ✓"]:::redM
  classDef yel fill:#fef3c7,stroke:#d97706,color:#78350f
  classDef redD fill:#f87171,stroke:#dc2626,color:#7f1d1d,font-weight:700
  classDef redM fill:#dc2626,stroke:#b91c1c,color:#fff,font-weight:700
```

---

## Stage 1: The Hook — Company / Asset Overview

> *Mixed — LLM can draft narrative (🟡) but legal docs and capital structure are human-sourced (🔴). Compilation is 🟢.*

```mermaid
flowchart TB
  A["Draft overview: thesis, history, milestones"]:::yel --> B["Legal: Entity structure, jurisdiction"]:::red
  B --> C["Legal: Capital structure & ownership"]:::red
  C --> D["Finance: Headcount / operating footprint"]:::yel
  D --> E["Finance: Prior capital raises"]:::yel
  E --> F["Compile Section 2 — Overview"]:::grnC
  classDef red fill:#fecaca,stroke:#dc2626,color:#7f1d1d
  classDef yel fill:#fef3c7,stroke:#d97706,color:#78350f
  classDef grnC fill:#16a34a,stroke:#15803d,color:#fff,font-weight:700
```

---

## Stage 2: The Opportunity

> *Heavy 🟢 — market research, TAM modeling, competitive framing are LLM strengths. Customer/counterparty validation is 🔴.*

```mermaid
flowchart TB
  subgraph MKT["Section 3 · Market Opportunity"]
    direction TB
    M1["TAM: top-down from industry data"]:::grn --> M2["TAM: bottom-up from addressable accounts"]:::yel
    M2 --> M3["Reconcile top-down & bottom-up"]:::grn
    M3 --> M4["Define SAM & SOM"]:::grn
    M4 --> M5["Document 2–4 sector tailwinds"]:::grn
    M5 --> M6["Regulatory & macro landscape"]:::grn
    M6 --> M7["Compile Section 3"]:::grnC
  end
  subgraph PROB["Section 4 · Value Proposition"]
    direction TB
    P1["Quantify target pain / unmet need"]:::yel --> P2["Document current alternatives"]:::grn
    P2 --> P3["Present core value delivery mechanism"]:::yel
    P3 --> P4["Customer / counterparty validation"]:::red
    P4 --> P5["Compile Section 4"]:::grnC
  end
  subgraph BIZ["Section 5 · Business Model"]
    direction TB
    B1["Revenue model: streams, pricing, contracts"]:::yel --> B2["Unit economics: margins, payback, ROI"]:::yel
    B2 --> B3["Gross / contribution margin profile"]:::yel
    B3 --> B4["Revenue growth levers"]:::yel
    B4 --> B5["Compile Section 5"]:::grnC
  end
  MKT --> PROB --> BIZ
  classDef red fill:#fecaca,stroke:#dc2626,color:#7f1d1d
  classDef yel fill:#fef3c7,stroke:#d97706,color:#78350f
  classDef grn fill:#dcfce7,stroke:#16a34a,color:#14532d
  classDef grnC fill:#16a34a,stroke:#15803d,color:#fff,font-weight:700
```

---

## Stage 3: The Proof

> *Mixed — LLM computes growth rates and builds frameworks (🟢), but raw operating data needs human extraction (🟡). Win/loss data is 🔴.*

```mermaid
flowchart TB
  subgraph TRAC["Section 6 · Traction & Key Metrics"]
    direction TB
    T1["Pull revenue trajectory"]:::yel --> T2["Calculate growth rates: YoY, QoQ"]:::grn
    T2 --> T3["Customer / account count & attrition"]:::yel
    T3 --> T4["Retention & renewal rates"]:::yel
    T4 --> T5["Capital efficiency: burn, ROIC, rev/employee"]:::grn
    T5 --> T6["Pipeline / backlog coverage"]:::yel
    T6 --> T7["Compile Section 6"]:::grnC
  end
  subgraph COMP["Section 7 · Competitive Landscape"]
    direction TB
    C1["Build competitive positioning map"]:::grn --> C2["Win/loss or bid data vs. competitors"]:::red
    C2 --> C3["Document moats & defensibility"]:::grn
    C3 --> C4["Compile Section 7"]:::grnC
  end
  subgraph GTM["Section 8 · Origination & Distribution"]
    direction TB
    G1x["Define origination strategy"]:::yel --> G2x["Conversion rates by stage"]:::yel
    G2x --> G3x["Productivity metrics: cycle, ramp, capacity"]:::yel
    G3x --> G4x["Origination efficiency by channel"]:::yel
    G4x --> G5x["Compile Section 8"]:::grnC
  end
  TRAC --> COMP --> GTM
  classDef red fill:#fecaca,stroke:#dc2626,color:#7f1d1d
  classDef yel fill:#fef3c7,stroke:#d97706,color:#78350f
  classDef grn fill:#dcfce7,stroke:#16a34a,color:#14532d
  classDef grnC fill:#16a34a,stroke:#15803d,color:#fff,font-weight:700
```

---

## Stage 4: The Team

> *🟡 throughout — LLM can draft profiles, but retention data (🔴) and investor commitments (🔴) are proprietary.*

```mermaid
flowchart TB
  A["Draft management team profiles"]:::yel --> B["Org structure & operating footprint"]:::yel
  B --> C["Key hires / investments planned"]:::yel
  C --> D["Retention data: turnover, tenure"]:::red
  D --> E["Compile Section 9 — Team"]:::grnC
  E --> F["Board / governance composition"]:::yel
  F --> G["Advisors & strategic relationships"]:::yel
  G --> H["Existing investor follow-on intent"]:::red
  H --> I["Compile Section 10 — Governance"]:::grnC
  classDef red fill:#fecaca,stroke:#dc2626,color:#7f1d1d
  classDef yel fill:#fef3c7,stroke:#d97706,color:#78350f
  classDef grnC fill:#16a34a,stroke:#15803d,color:#fff,font-weight:700
```

---

## 🚧 Gate 2: Financial Reconciliation & Controls

> *v3.1: Expanded with 4 mandatory finance controls — rounding policy, variance tolerance by line item, single source of truth, and non-GAAP reconciliation.*

```mermaid
flowchart LR
  A["Map figures to model cells"]:::yel --> B["Reconcile to audited actuals"]:::red
  B --> C["Verify consistency across sections"]:::yel
  C --> R["Apply rounding policy"]:::yel
  R --> V["Check variance tolerance by line item"]:::yel
  V --> S["Confirm single source of truth model"]:::red
  S --> N["Reconcile non-GAAP / adjusted metrics"]:::yel
  N --> D{"All layers pass?"}:::redD
  D -- No --> A
  D -- Yes --> E["Finance Owner: ATTESTATION ✓ | Memo Owner: CERTIFICATION ✓"]:::redM
  classDef red fill:#fecaca,stroke:#dc2626,color:#7f1d1d
  classDef yel fill:#fef3c7,stroke:#d97706,color:#78350f
  classDef redD fill:#f87171,stroke:#dc2626,color:#7f1d1d,font-weight:700
  classDef redM fill:#dc2626,stroke:#b91c1c,color:#fff,font-weight:700
```

---

## Stage 5: The Numbers

> *🟡 for formatting historicals (needs data fed in). 🟢 for scenario modeling once assumptions are set. v3.1: Governed assumptions with owner + date + plan tie-out required.*

```mermaid
flowchart TB
  subgraph HIST["Section 11 · Historical Financials"]
    direction TB
    H1["P&L: 2–3 fiscal years"]:::yel --> H2["Balance sheet & working capital"]:::yel
    H2 --> H3["Cash flow & non-recurring items"]:::yel
    H3 --> H4["Quarterly / seasonal trends"]:::yel
    H4 --> H5["Compile Section 11"]:::grnC
  end
  subgraph PROJ["Section 12 · Projections"]
    direction TB
    F1["3–5 year financial forecast"]:::yel --> F2["Governed assumptions: owner + date + source"]:::yel
    F2 --> F3["Scenarios: base / bull / bear (by drivers)"]:::grn
    F3 --> F4["Revenue bridge or growth decomposition"]:::grn
    F4 --> F5["Path to profitability / target returns"]:::grn
    F5 --> FT["Tie assumptions to operating / hiring / capex plan"]:::yel
    FT --> F6["Compile Section 12"]:::grnC
  end
  subgraph CASH["Section 13 · Liquidity & Capital Needs"]
    direction TB
    R1["Current cash / available liquidity"]:::red --> R2["Cash consumption or debt service"]:::yel
    R2 --> R3["Runway, covenant headroom, or coverage"]:::grn
    R3 --> R4["Sources & uses waterfall"]:::grn
    R4 --> R5["Capital allocation plan"]:::yel
    R5 --> R6["Compile Section 13"]:::grnC
  end
  HIST --> PROJ --> CASH
  classDef red fill:#fecaca,stroke:#dc2626,color:#7f1d1d
  classDef yel fill:#fef3c7,stroke:#d97706,color:#78350f
  classDef grn fill:#dcfce7,stroke:#16a34a,color:#14532d
  classDef grnC fill:#16a34a,stroke:#15803d,color:#fff,font-weight:700
```

---

## 🚧 Gate 3: Capital Structure & Legal Reconciliation

> *Almost entirely 🔴 — ownership, obligations, and counsel sign-off are human-only. Pro forma math is 🟡.*

```mermaid
flowchart LR
  A["Verify ownership & capital structure"]:::red --> B["Verify instruments & obligations"]:::red
  B --> C["Pro forma post-transaction"]:::yel
  C --> D["External counsel confirms"]:::red
  D --> E{"Fully reconciled?"}:::redD
  E -- No --> A
  E -- Yes --> F["Legal Owner: ATTESTATION ✓"]:::redM
  F --> G["External Counsel: PREREQUISITE ✓ (if required)"]:::redM
  classDef red fill:#fecaca,stroke:#dc2626,color:#7f1d1d
  classDef yel fill:#fef3c7,stroke:#d97706,color:#78350f
  classDef redD fill:#f87171,stroke:#dc2626,color:#7f1d1d,font-weight:700
  classDef redM fill:#dc2626,stroke:#b91c1c,color:#fff,font-weight:700
```

---

## ⚠ Decision-Rights Freeze — Required Before The Ask

> *New in v3.1 — entirely 🔴. Before drafting Sections 14–15, the Deal Sponsor must lock five decision parameters. This prevents late-stage rewrites and internal inconsistency between the ask and the analysis.*

```mermaid
flowchart LR
  DR1["Lock exact IC decision requested"]:::red --> DR2["Define negotiable vs non-negotiable terms"]:::red
  DR2 --> DR3["Delegate negotiation authority & band"]:::red
  DR3 --> DR4["Set return-to-IC triggers"]:::red
  DR4 --> DR5["Lock target valuation range"]:::red
  DR5 --> DR6{"All parameters locked?"}:::redD
  DR6 -- No --> DR1
  DR6 -- Yes --> DR7["Deal Sponsor: APPROVAL ✓"]:::redM
  classDef red fill:#fecaca,stroke:#dc2626,color:#7f1d1d
  classDef redD fill:#f87171,stroke:#dc2626,color:#7f1d1d,font-weight:700
  classDef redM fill:#dc2626,stroke:#b91c1c,color:#fff,font-weight:700
```

---

## Stage 6: The Ask

> *Section 14 (deal terms) is mostly 🔴. Section 15 (valuation) is mostly 🟢. v3.1: Adds valuation method applicability check — not all methods apply to every deal.*

```mermaid
flowchart TB
  subgraph RAISE["Section 14 · Transaction Terms"]
    direction TB
    R1["Transaction size & structure"]:::red --> R2["Valuation basis: EV, pre/post, asset-level"]:::red
    R2 --> R3["Use of proceeds / capital deployment"]:::yel
    R3 --> R4["Pro forma ownership / leverage impact"]:::yel
    R4 --> R5["Timeline & existing commitments"]:::red
    R5 --> R6{"Complex transaction mechanics?"}:::redD
    R6 -- Yes --> R7["Co-invest, secondary, syndication detail"]:::red
    R6 -- No --> R8["Compile Section 14"]:::grnC
    R7 --> R8
  end
  subgraph VAL["Section 15 · Valuation Support"]
    direction TB
    VX{"Select applicable valuation methods"}:::yelD --> V1["Comparable companies (if comps exist)"]:::grn
    V1 --> V2["Precedent transactions (if recent)"]:::grn
    V2 --> V3["Multiple analysis: EV/Rev, EV/EBITDA, P/E"]:::grn
    V3 --> V4{"DCF / LBO / Cap Rate applicable?"}:::yelD
    V4 -- Yes --> V5["Build applicable model"]:::grn
    V4 -- No --> V6["Triangulate range from available methods"]:::grn
    V5 --> V6
    V6 --> V7["Internal: floor / target / ceiling"]:::red
    V7 --> V8["Market conditions & comp refresh date"]:::grn
    V8 --> V9["Compile Section 15"]:::grnC
  end
  RAISE --> VAL
  classDef red fill:#fecaca,stroke:#dc2626,color:#7f1d1d
  classDef redD fill:#f87171,stroke:#dc2626,color:#7f1d1d,font-weight:700
  classDef yel fill:#fef3c7,stroke:#d97706,color:#78350f
  classDef yelD fill:#fbbf24,stroke:#d97706,color:#78350f,font-weight:700
  classDef grn fill:#dcfce7,stroke:#16a34a,color:#14532d
  classDef grnC fill:#16a34a,stroke:#15803d,color:#fff,font-weight:700
```

---

## Stage 7: Risk & Close

> *Risk identification is fully 🟢. Value creation plan needs human input (🟡). Appendix index is 🟢.*

```mermaid
flowchart TB
  subgraph RISK["Section 16 · Risks & Mitigants"]
    direction TB
    K1["Market & macro risks"]:::grn --> K2["Execution & operating risks"]:::grn
    K2 --> K3["Financial & structural risks"]:::grn
    K3 --> K4["Regulatory & legal risks"]:::grn
    K4 --> K5["Pair each with specific mitigant"]:::grn
    K5 --> K6["Compile Section 16"]:::grnC
  end
  subgraph MILE["Section 17 · Value Creation Plan"]
    direction TB
    M1["12–24 month milestone plan"]:::yel --> M2["Key value inflection triggers"]:::yel
    M2 --> M3["Long-term thesis & exit paths"]:::yel
    M3 --> M4["Compile Section 17"]:::grnC
  end
  subgraph APPX["Section 18 · Appendices"]
    direction TB
    A1["Build appendix index"]:::grn --> A2["Confidentiality tiering"]:::yel
    A2 --> A3["Compile Section 18"]:::grnC
  end
  RISK --> MILE --> APPX
  classDef yel fill:#fef3c7,stroke:#d97706,color:#78350f
  classDef grn fill:#dcfce7,stroke:#16a34a,color:#14532d
  classDef grnC fill:#16a34a,stroke:#15803d,color:#fff,font-weight:700
```

---

## ⭐ Executive Summary — Written Last

> *Fully 🟢 — once all sections are finalized, the LLM can synthesize the exec summary independently.*

```mermaid
flowchart LR
  A["1-sentence investment thesis"]:::grn --> B["3–5 headline KPIs"]:::grn
  B --> C["Transaction size, valuation, use of proceeds"]:::grn
  C --> D["Forward-looking value creation statement"]:::grn
  D --> E["Compile Section 1 — max 1 page"]:::grnC
  classDef grn fill:#dcfce7,stroke:#16a34a,color:#14532d
  classDef grnC fill:#16a34a,stroke:#15803d,color:#fff,font-weight:700
```

---

## 🚧 Gate 4: Appendix Completeness

> *Claim review is 🟢. Reference and exhibit verification is 🔴. v3.1: Memo Owner signs as CERTIFICATION (production readiness).*

```mermaid
flowchart LR
  A["Review claims for data support"]:::grn --> B{"Every claim supported?"}:::yelD
  B -- No --> C["Add evidence OR remove claim"]:::yel
  C --> A
  B -- Yes --> D["Verify references cleared"]:::red
  D --> E["Verify exhibits current"]:::red
  E --> F["Verify data sources cited"]:::grn
  F --> G["Memo Owner: CERTIFICATION ✓"]:::redM
  classDef red fill:#fecaca,stroke:#dc2626,color:#7f1d1d
  classDef yel fill:#fef3c7,stroke:#d97706,color:#78350f
  classDef yelD fill:#fbbf24,stroke:#d97706,color:#78350f,font-weight:700
  classDef grn fill:#dcfce7,stroke:#16a34a,color:#14532d
  classDef redM fill:#dc2626,stroke:#b91c1c,color:#fff,font-weight:700
```

---

## ✅ Decision & Approval Block — Section 19

> *Mostly 🔴 — IC-level decisions. v3.1: Adds internal-only content flagging step before compilation.*

```mermaid
flowchart LR
  A["Draft IC decision requested"]:::red --> B["Conditions & non-negotiables"]:::red
  B --> C["Acceptable negotiation range"]:::red
  C --> D["Fallback plan with impact analysis"]:::yel
  D --> E["Escalation triggers"]:::yel
  E --> F["Internal-only content flagged"]:::yel
  F --> G["Compile Section 19"]:::grnC
  classDef red fill:#fecaca,stroke:#dc2626,color:#7f1d1d
  classDef yel fill:#fef3c7,stroke:#d97706,color:#78350f
  classDef grnC fill:#16a34a,stroke:#15803d,color:#fff,font-weight:700
```

---

## 🚧 Gate 5: Final Sign-Off & Pre-Submission QC

> *v3.1: Expanded with non-GAAP verification, internal-only redaction check, memo version metadata check. Sign-offs now carry explicit types.*

```mermaid
flowchart TB
  subgraph QC["Pre-Submission Checklist"]
    direction TB
    Q1["Financials match single source model"]:::yel --> Q2["KPIs consistent across sections"]:::grn
    Q2 --> Q3["Cash matches trailing actuals"]:::yel
    Q3 --> Q4["Capital plan ties to operating plan"]:::grn
    Q4 --> Q5["Comps refreshed & methods appropriate"]:::yel
    Q5 --> Q6["Confidential references cleared"]:::red
    Q6 --> Q7["Risk disclosures reviewed by Legal"]:::red
    Q7 --> Q8["Page budget enforced"]:::grn
    Q8 --> Q9["Appendix index versioned"]:::grn
    Q9 --> Q10["Non-GAAP reconciliation verified"]:::yel
    Q10 --> Q11["Internal-only content redacted from ext version"]:::red
    Q11 --> Q12["Memo version metadata complete"]:::yel
  end
  Q12 --> PASS{"All checks pass?"}:::redD
  PASS -- No --> Q1
  PASS -- Yes --> S1x["Finance Owner: ATTESTATION ✓"]:::redM
  S1x --> S2x["Legal Owner: ATTESTATION ✓"]:::redM
  S2x --> S3x["Memo Owner: CERTIFICATION ✓"]:::redM
  S3x --> S4x["Deal Sponsor: APPROVAL ✓"]:::redM
  S4x --> DONE(["🚀 MEMO CLEARED FOR IC DISTRIBUTION"]):::redM
  classDef red fill:#fecaca,stroke:#dc2626,color:#7f1d1d
  classDef redD fill:#f87171,stroke:#dc2626,color:#7f1d1d,font-weight:700
  classDef redM fill:#dc2626,stroke:#b91c1c,color:#fff,font-weight:700
  classDef yel fill:#fef3c7,stroke:#d97706,color:#78350f
  classDef grn fill:#dcfce7,stroke:#16a34a,color:#14532d
```

---

## Capability Summary

| Category | Approx. Steps | Examples |
|---|:---:|---|
| 🔴 **LLM Cannot Do** | ~62 | Sign-offs, personnel assignments, deal terms, actuals reconciliation, confidentiality clearance, capital structure verification, decision-rights freeze, IC decisions |
| 🟡 **LLM Needs Human Assistance** | ~66 | Draft narratives from data, compute metrics from inputs, propose KPI definitions, format financials, governed assumptions, build projections, rounding/variance checks |
| 🟢 **LLM Can Do** | ~56 | Market research & TAM, comp analysis, scenario modeling, risk frameworks, revenue bridges, DCF/LBO, section compilation, exec summary, consistency checks |

---

## v3.1 Process Controls Summary

| Control | Description |
|---|---|
| **Ownership Hierarchy** | Memo Owner = single accountable; Deal Sponsor = final approver; functional owners = domain attestation |
| **Sign-Off Semantics** | Four defined types: Attestation, Certification, Approval, Prerequisite |
| **Version Control** | Memo-level: version number, date, owner, change summary, status |
| **Change Control** | Gate re-open rules for 6 trigger events; material changes require new version + re-attestation |
| **Decision-Rights Freeze** | 5 parameters locked before The Ask: decision, negotiables, authority, triggers, valuation range |
| **Finance Controls** | Rounding policy, variance tolerance by line item, single source of truth, non-GAAP reconciliation |
| **Assumption Governance** | Every projection assumption requires: owner, source, date, and plan tie-out |
| **Valuation Applicability** | Method must be justified by asset class and data availability; inappropriate methods flagged |
| **Distribution Controls** | Internal-only content redacted from external versions; -EXT suffix; Deal Sponsor approves external version |

---

## Usage

**GitHub** — Push this `README.md` for native Mermaid rendering with capability colors.

**Interactive** — Paste charts at [mermaid.live](https://mermaid.live)

**Presentation** — Open `index.html` (or `ic_memo_workflow_presentation.html`) for the dark-mode scroll-animated version.

---

*IC Production Blueprint v3.1 · Generalized · Process Controls · LLM Capability Map · Confidential*
