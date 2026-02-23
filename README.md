# IC Memo Production Workflow — LLM Capability Map

### Generalized Investment Committee Memo — Blueprint v2.0

> **164 actionable steps** · **7 stages** · **5 validation gates** · **19 content sections**
> Asset-class agnostic: venture, growth equity, PE, credit, real assets.
> Every step classified by what an LLM can and cannot do.

---

## LLM Capability Legend

| Color | Meaning | Description |
|:---:|---|---|
| 🔴 | **LLM Cannot Do** | Requires human judgment, proprietary data access, legal authority, or physical sign-off |
| 🟡 | **LLM Needs Human Assistance** | LLM can draft/compute but needs human to supply data, validate, or approve output |
| 🟢 | **LLM Can Do** | LLM can execute independently given prior context and data from earlier steps |

---

## Pre-Production: Transaction Intake

> *Mostly 🔴 — these are deal sponsor decisions that set every downstream parameter.*

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

> *Mostly 🔴 — personnel assignments and deal structure decisions are human-only.*

```mermaid
flowchart TB
  P09["Assign Memo Owner"]:::red --> P10["Assign Financial Data Owner"]:::red
  P10 --> P11["Assign Legal / Capital Structure Owner"]:::red
  P11 --> P12["Assign Commercial / Operating Owner"]:::red
  P12 --> P13["Resolve scoping decisions with Deal Sponsor"]:::red
  P13 --> P14{"Co-invest / secondary component?"}:::redD
  P14 -- Yes --> P15["Document co-investors & allocation"]:::red
  P14 -- No --> P16{"Existing investor participation?"}:::redD
  P15 --> P16
  P16 -- Yes --> P17["Document follow-on commitments"]:::red
  P16 -- No --> P18["Confirm syndication strategy"]:::red
  P17 --> P18
  P18 --> P19["Finalize page budget"]:::yel
  classDef red fill:#fecaca,stroke:#dc2626,color:#7f1d1d
  classDef redD fill:#f87171,stroke:#dc2626,color:#7f1d1d,font-weight:700
  classDef yel fill:#fef3c7,stroke:#d97706,color:#78350f
```

---

## 🚧 Gate 1: KPI & Metrics Definition Lock

> *🟡 LLM can propose standard definitions, but Finance must confirm methodology and sign off (🔴).*

```mermaid
flowchart LR
  A["Define revenue recognition methodology"]:::yel --> B["Define retention / renewal rate calc"]:::yel
  B --> C["Define attrition: customer vs. revenue"]:::yel
  C --> D["Define origination cost scope"]:::yel
  D --> E{"All definitions locked?"}:::redD
  E -- No --> A
  E -- Yes --> F["Financial Data Owner: SIGN-OFF ✓"]:::redM
  classDef yel fill:#fef3c7,stroke:#d97706,color:#78350f
  classDef redD fill:#f87171,stroke:#dc2626,color:#7f1d1d,font-weight:700
  classDef redM fill:#dc2626,stroke:#b91c1c,color:#fff,font-weight:700
```

---

## Stage 1: The Hook — Company / Asset Overview

> *Mixed — LLM can draft narrative (🟡) but legal docs and capital structure are human-sourced (🔴). Compilation is 🟢.*

```mermaid
flowchart TB
  A["Draft overview: thesis, history, milestones"]:::yel --> B["Legal: Entity structure, jurisdiction, subs"]:::red
  B --> C["Legal: Capital structure & ownership summary"]:::red
  C --> D["Finance: Headcount / operating footprint"]:::yel
  D --> E["Finance: Prior capital raises or transactions"]:::yel
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

## 🚧 Gate 2: Financial Reconciliation

> *Reconciliation to audited actuals is 🔴. Cross-checking consistency is 🟡. Sign-off always 🔴.*

```mermaid
flowchart LR
  A["Map memo figures to model cells"]:::yel --> B["Reconcile model to audited actuals"]:::red
  B --> C["Verify internal consistency across sections"]:::yel
  C --> D{"All reconciliation layers pass?"}:::redD
  D -- No --> A
  D -- Yes --> E["Finance + Memo Owner: JOINT SIGN-OFF ✓"]:::redM
  classDef red fill:#fecaca,stroke:#dc2626,color:#7f1d1d
  classDef yel fill:#fef3c7,stroke:#d97706,color:#78350f
  classDef redD fill:#f87171,stroke:#dc2626,color:#7f1d1d,font-weight:700
  classDef redM fill:#dc2626,stroke:#b91c1c,color:#fff,font-weight:700
```

---

## Stage 5: The Numbers

> *🟡 for formatting historicals (needs data fed in). 🟢 for scenario modeling, bridges, and return analysis once assumptions are set.*

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
    F1["3–5 year financial forecast"]:::yel --> F2["Key assumptions documented"]:::yel
    F2 --> F3["Scenario analysis: base / bull / bear"]:::grn
    F3 --> F4["Revenue bridge or growth decomposition"]:::grn
    F4 --> F5["Path to profitability / target returns"]:::grn
    F5 --> F6["Compile Section 12"]:::grnC
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
  A["Verify ownership & capital structure"]:::red --> B["Verify dilutive instruments & debt obligations"]:::red
  B --> C["Pro forma post-transaction"]:::yel
  C --> D["External counsel confirms all obligations"]:::red
  D --> E{"Fully reconciled?"}:::redD
  E -- No --> A
  E -- Yes --> F["Legal + Counsel: SIGN-OFF ✓"]:::redM
  classDef red fill:#fecaca,stroke:#dc2626,color:#7f1d1d
  classDef yel fill:#fef3c7,stroke:#d97706,color:#78350f
  classDef redD fill:#f87171,stroke:#dc2626,color:#7f1d1d,font-weight:700
  classDef redM fill:#dc2626,stroke:#b91c1c,color:#fff,font-weight:700
```

---

## Stage 6: The Ask

> *Section 14 (deal terms) is mostly 🔴. Section 15 (valuation) is mostly 🟢 — comp analysis, DCF/LBO, and triangulation are LLM strengths. Internal pricing is 🔴.*

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
    V1["Comparable companies: 5–8 comps"]:::grn --> V2["Precedent transactions"]:::grn
    V2 --> V3["Multiple analysis: EV/Revenue, EV/EBITDA, P/E"]:::grn
    V3 --> V4{"DCF / LBO applicable?"}:::yelD
    V4 -- Yes --> V5["Build DCF or LBO model"]:::grn
    V4 -- No --> V6["Triangulate valuation range"]:::grn
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

> *Risk identification is fully 🟢. Value creation plan needs human input (🟡) because it reflects forward commitments. Appendix index is 🟢.*

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

> *Claim review is 🟢. Reference and exhibit verification is 🔴 (requires live system access). Sign-off always 🔴.*

```mermaid
flowchart LR
  A["Review claims for data support"]:::grn --> B{"Every claim supported?"}:::yelD
  B -- No --> C["Add evidence OR remove claim"]:::yel
  C --> A
  B -- Yes --> D["Verify references cleared"]:::red
  D --> E["Verify exhibits current"]:::red
  E --> F["Verify data sources cited"]:::grn
  F --> G["Memo Owner: SIGN-OFF ✓"]:::redM
  classDef red fill:#fecaca,stroke:#dc2626,color:#7f1d1d
  classDef yel fill:#fef3c7,stroke:#d97706,color:#78350f
  classDef yelD fill:#fbbf24,stroke:#d97706,color:#78350f,font-weight:700
  classDef grn fill:#dcfce7,stroke:#16a34a,color:#14532d
  classDef redM fill:#dc2626,stroke:#b91c1c,color:#fff,font-weight:700
```

---

## ✅ Decision & Approval Block — Section 19

> *Mostly 🔴 — IC-level decisions. LLM can draft fallback analysis (🟡) and compile (🟢).*

```mermaid
flowchart LR
  A["Draft IC decision requested"]:::red --> B["Conditions & non-negotiables"]:::red
  B --> C["Acceptable negotiation range"]:::red
  C --> D["Fallback plan with impact analysis"]:::yel
  D --> E["Escalation triggers"]:::yel
  E --> F["Compile Section 19"]:::grnC
  classDef red fill:#fecaca,stroke:#dc2626,color:#7f1d1d
  classDef yel fill:#fef3c7,stroke:#d97706,color:#78350f
  classDef grnC fill:#16a34a,stroke:#15803d,color:#fff,font-weight:700
```

---

## 🚧 Gate 5: Final Sign-Off & Pre-Submission QC

> *QC checks are a mix: consistency checks 🟢, data freshness 🟡, legal clearance 🔴. All sign-offs are 🔴.*

```mermaid
flowchart TB
  subgraph QC["Pre-Submission Checklist"]
    direction TB
    Q1["Financials match model"]:::yel --> Q2["KPIs consistent across sections"]:::grn
    Q2 --> Q3["Cash figures match trailing actuals"]:::yel
    Q3 --> Q4["Capital plan ties to operating plan"]:::grn
    Q4 --> Q5["Comps / market data refreshed"]:::yel
    Q5 --> Q6["Confidential references cleared"]:::red
    Q6 --> Q7["Risk disclosures reviewed by Legal"]:::red
    Q7 --> Q8["Page budget enforced"]:::grn
    Q8 --> Q9["Appendix index versioned"]:::grn
  end
  Q9 --> PASS{"All checks pass?"}:::redD
  PASS -- No --> Q1
  PASS -- Yes --> S1x["Financial Data Owner ✓"]:::redM
  S1x --> S2x["Legal / Capital Structure Owner ✓"]:::redM
  S2x --> S3x["Deal Sponsor ✓"]:::redM
  S3x --> S4x["Memo Owner ✓"]:::redM
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
| 🔴 **LLM Cannot Do** | ~55 | Sign-offs, personnel assignments, deal terms, actuals reconciliation, confidentiality clearance, capital structure verification, IC decisions |
| 🟡 **LLM Needs Human Assistance** | ~60 | Draft narratives from data, compute metrics from fed inputs, propose KPI definitions, format financials, build projections from assumptions |
| 🟢 **LLM Can Do** | ~49 | Market research & TAM, comp analysis, scenario modeling, risk frameworks, revenue bridges, DCF/LBO, section compilation, exec summary, consistency checks |

---

*IC Production Blueprint v3.0 · Generalized · LLM Capability Map · Confidential*
