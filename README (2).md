# IC Memo Production Workflow — LLM Capability Map

### Company-Side Fundraising Memo — Blueprint v2.0

> **100+ action steps** · **7 stages** · **5 validation gates** · **18 content sections**
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

> *Mostly 🔴 — these are executive decisions that set the parameters for everything downstream.*

```mermaid
flowchart LR
  P01(["CEO: Initiate memo production"]):::red --> P02["Define transaction type"]:::red
  P02 --> P03["Set round size & range"]:::red
  P03 --> P04["Establish valuation basis"]:::yel
  P04 --> P05["Document decision required"]:::yel
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
  P10 --> P11["Assign Legal / Cap Table Owner"]:::red
  P11 --> P12["Assign Product / GTM Owner"]:::red
  P12 --> P13["Resolve scoping decisions with CEO"]:::red
  P13 --> P14{"Secondary liquidity?"}:::redD
  P14 -- Yes --> P15["Document sellers & amount"]:::red
  P14 -- No --> P16{"Insider participation?"}:::redD
  P15 --> P16
  P16 -- Yes --> P17["Document pro rata commitments"]:::red
  P16 -- No --> P18["Confirm syndicate strategy"]:::red
  P17 --> P18
  P18 --> P19["Finalize page budget"]:::yel
  classDef red fill:#fecaca,stroke:#dc2626,color:#7f1d1d
  classDef redD fill:#f87171,stroke:#dc2626,color:#7f1d1d,font-weight:700
  classDef yel fill:#fef3c7,stroke:#d97706,color:#78350f
```

---

## 🚧 Gate 1: Metrics Definition Lock

> *🟡 LLM can propose standard definitions, but Finance must confirm methodology and sign off (🔴).*

```mermaid
flowchart LR
  A["Define ARR methodology"]:::yel --> B["Define NRR calculation"]:::yel
  B --> C["Define churn: logo vs. revenue"]:::yel
  C --> D["Define CAC scope"]:::yel
  D --> E{"All definitions locked?"}:::redD
  E -- No --> A
  E -- Yes --> F["Financial Data Owner: SIGN-OFF ✓"]:::redM
  classDef yel fill:#fef3c7,stroke:#d97706,color:#78350f
  classDef redD fill:#f87171,stroke:#dc2626,color:#7f1d1d,font-weight:700
  classDef redM fill:#dc2626,stroke:#b91c1c,color:#fff,font-weight:700
```

---

## Stage 1: The Hook — Company Overview

> *Mixed — LLM can draft narrative (🟡) but legal docs and cap table are human-sourced (🔴). Compilation is 🟢.*

```mermaid
flowchart TB
  A["Draft Company Overview: mission, founding, milestones"]:::yel --> B["Legal: Corporate structure — entity, jurisdiction"]:::red
  B --> C["Legal: Cap table summary — founders / pool / investors"]:::red
  C --> D["Finance: Headcount breakdown by function"]:::yel
  D --> E["Finance: Prior funding summary — round, amount, lead"]:::yel
  E --> F["Compile Section 2 — Company Overview"]:::grnC
  classDef red fill:#fecaca,stroke:#dc2626,color:#7f1d1d
  classDef yel fill:#fef3c7,stroke:#d97706,color:#78350f
  classDef grnC fill:#16a34a,stroke:#15803d,color:#fff,font-weight:700
```

---

## Stage 2: The Opportunity

> *Heavy 🟢 — market research, TAM modeling, competitive framing are LLM strengths. Customer validation (NPS, quotes) is 🔴.*

```mermaid
flowchart TB
  subgraph MKT["Section 3 · Market Opportunity"]
    direction TB
    M1["TAM: top-down from industry reports"]:::grn --> M2["TAM: bottom-up from customers × ACV"]:::yel
    M2 --> M3["Reconcile top-down & bottom-up"]:::grn
    M3 --> M4["Define SAM & SOM"]:::grn
    M4 --> M5["Document 2–4 market tailwinds"]:::grn
    M5 --> M6["Address regulatory landscape"]:::grn
    M6 --> M7["Compile Section 3"]:::grnC
  end
  subgraph PROB["Section 4 · Problem & Solution"]
    direction TB
    P1["Quantify customer pain in $ / hours"]:::yel --> P2["Document current alternatives"]:::grn
    P2 --> P3["Present core solution mechanism"]:::yel
    P3 --> P4["Customer validation: NPS, quotes"]:::red
    P4 --> P5["Compile Section 4"]:::grnC
  end
  subgraph BIZ["Section 5 · Business Model"]
    direction TB
    B1["Revenue model: pricing, billing"]:::yel --> B2["Unit economics: LTV, CAC, payback"]:::yel
    B2 --> B3["Gross margin profile & trend"]:::yel
    B3 --> B4["Expansion revenue mechanics"]:::yel
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

> *Mixed — LLM computes growth rates and builds frameworks (🟢), but raw CRM/pipeline data needs human extraction (🟡). Win/loss data is 🔴.*

```mermaid
flowchart TB
  subgraph TRAC["Section 6 · Traction & Key Metrics"]
    direction TB
    T1["Pull ARR/MRR trajectory"]:::yel --> T2["Calculate YoY & QoQ growth rates"]:::grn
    T2 --> T3["Customer count & logo churn"]:::yel
    T3 --> T4["NRR & gross retention from cohorts"]:::yel
    T4 --> T5["Burn multiple, rev per employee"]:::grn
    T5 --> T6["Pipeline as multiple of quota"]:::yel
    T6 --> T7["Compile Section 6"]:::grnC
  end
  subgraph COMP["Section 7 · Competitive Landscape"]
    direction TB
    C1["Build 2×2 competitive map"]:::grn --> C2["Win/loss data against competitors"]:::red
    C2 --> C3["Document moats: switching costs, IP"]:::grn
    C3 --> C4["Compile Section 7"]:::grnC
  end
  subgraph GTM["Section 8 · Go-to-Market"]
    direction TB
    G1x["Define sales motion"]:::yel --> G2x["Funnel conversion rates"]:::yel
    G2x --> G3x["Quota attainment, ramp, cycle"]:::yel
    G3x --> G4x["Magic number & CAC by channel"]:::yel
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

> *🟡 throughout — LLM can draft profiles from bios, but actual retention data (🔴) and follow-on commitments (🔴) are proprietary.*

```mermaid
flowchart TB
  A["Draft founder & C-suite profiles"]:::yel --> B["Org chart & headcount"]:::yel
  B --> C["Key hires planned with capital"]:::yel
  C --> D["Retention metrics: turnover, tenure"]:::red
  D --> E["Compile Section 9 — Team"]:::grnC
  E --> F["Board members & independence"]:::yel
  F --> G["Advisors & value provided"]:::yel
  G --> H["Investor follow-on commitments"]:::red
  H --> I["Compile Section 10 — Board"]:::grnC
  classDef red fill:#fecaca,stroke:#dc2626,color:#7f1d1d
  classDef yel fill:#fef3c7,stroke:#d97706,color:#78350f
  classDef grnC fill:#16a34a,stroke:#15803d,color:#fff,font-weight:700
```

---

## 🚧 Gate 2: Financial Reconciliation

> *GL reconciliation is 🔴 (requires system access). Cross-checking consistency is 🟡. Sign-off always 🔴.*

```mermaid
flowchart LR
  A["Map memo figures to model cells"]:::yel --> B["Reconcile model to GL: less than 1%"]:::red
  B --> C["Verify consistency: S1 = S6 = S11"]:::yel
  C --> D{"All 3 layers pass?"}:::redD
  D -- No --> A
  D -- Yes --> E["Finance + Memo Owner: JOINT SIGN-OFF ✓"]:::redM
  classDef red fill:#fecaca,stroke:#dc2626,color:#7f1d1d
  classDef yel fill:#fef3c7,stroke:#d97706,color:#78350f
  classDef redD fill:#f87171,stroke:#dc2626,color:#7f1d1d,font-weight:700
  classDef redM fill:#dc2626,stroke:#b91c1c,color:#fff,font-weight:700
```

---

## Stage 5: The Numbers

> *🟡 for formatting historicals (needs data fed in). 🟢 for scenario modeling, revenue bridges, runway math once assumptions are set.*

```mermaid
flowchart TB
  subgraph HIST["Section 11 · Historical Financials"]
    direction TB
    H1["P&L: 2–3 FY"]:::yel --> H2["Balance sheet"]:::yel
    H2 --> H3["Cash flow & non-recurring"]:::yel
    H3 --> H4["Quarterly trends"]:::yel
    H4 --> H5["Compile Section 11"]:::grnC
  end
  subgraph PROJ["Section 12 · Projections"]
    direction TB
    F1["3–5yr revenue forecast"]:::yel --> F2["Key assumptions"]:::yel
    F2 --> F3["Scenario analysis: base/bull/bear"]:::grn
    F3 --> F4["Revenue bridge"]:::grn
    F4 --> F5["Path to profitability & FCF"]:::grn
    F5 --> F6["Compile Section 12"]:::grnC
  end
  subgraph CASH["Section 13 · Cash & Runway"]
    direction TB
    R1["Current cash position"]:::red --> R2["Burn rate: trailing 3-month"]:::yel
    R2 --> R3["Runway & post-raise runway"]:::grn
    R3 --> R4["Cash waterfall"]:::grn
    R4 --> R5["Milestone-to-capital mapping"]:::yel
    R5 --> R6["Compile Section 13"]:::grnC
  end
  HIST --> PROJ --> CASH
  classDef red fill:#fecaca,stroke:#dc2626,color:#7f1d1d
  classDef yel fill:#fef3c7,stroke:#d97706,color:#78350f
  classDef grn fill:#dcfce7,stroke:#16a34a,color:#14532d
  classDef grnC fill:#16a34a,stroke:#15803d,color:#fff,font-weight:700
```

---

## 🚧 Gate 3: Cap Table & Legal Reconciliation

> *Almost entirely 🔴 — cap table verification, legal obligations, and counsel sign-off are human-only. Pro forma math is 🟡.*

```mermaid
flowchart LR
  A["Verify ownership percentages"]:::red --> B["Verify pool & convertibles"]:::red
  B --> C["Pro forma post-raise"]:::yel
  C --> D["External counsel confirms"]:::red
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

> *Section 14 (raise terms) is mostly 🔴 — deal terms are CEO decisions. Section 15 (valuation) is mostly 🟢 — comp analysis, DCF, and triangulation are LLM core strengths. Internal pricing (floor/target/ceiling) is 🔴.*

```mermaid
flowchart TB
  subgraph RAISE["Section 14 · The Raise"]
    direction TB
    R1["Round size & structure"]:::red --> R2["Pre/post-money valuation"]:::red
    R2 --> R3["Use of proceeds"]:::yel
    R3 --> R4["Pro forma / dilution table"]:::yel
    R4 --> R5["Timeline & commitments"]:::red
    R5 --> R6{"Transaction mechanics?"}:::redD
    R6 -- Yes --> R7["Secondary, insider, syndicate"]:::red
    R6 -- No --> R8["Compile Section 14"]:::grnC
    R7 --> R8
  end
  subgraph VAL["Section 15 · Valuation Support"]
    direction TB
    V1["5–8 comparable companies"]:::grn --> V2["Precedent transactions"]:::grn
    V2 --> V3["Growth-adjusted multiples"]:::grn
    V3 --> V4{"DCF applicable?"}:::yelD
    V4 -- Yes --> V5["Build DCF"]:::grn
    V4 -- No --> V6["Triangulate valuation range"]:::grn
    V5 --> V6
    V6 --> V7["Internal: floor / target / ceiling"]:::red
    V7 --> V8["Market condition note"]:::grn
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

> *Risk identification and framing is fully 🟢. Milestones need human input (🟡) because they're forward commitments. Appendix index is 🟢.*

```mermaid
flowchart TB
  subgraph RISK["Section 16 · Risks & Mitigants"]
    direction TB
    K1["Market risks"]:::grn --> K2["Execution risks"]:::grn
    K2 --> K3["Financial risks"]:::grn
    K3 --> K4["Regulatory risks"]:::grn
    K4 --> K5["Pair each with mitigant"]:::grn
    K5 --> K6["Compile Section 16"]:::grnC
  end
  subgraph MILE["Section 17 · Milestones"]
    direction TB
    M1["12–18 month milestone plan"]:::yel --> M2["Next-round triggers"]:::yel
    M2 --> M3["Long-term vision & exits"]:::yel
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
  A["1-sentence company description"]:::grn --> B["3–5 finalized headline metrics"]:::grn
  B --> C["Round size, valuation, UoP"]:::grn
  C --> D["Forward-looking milestone"]:::grn
  D --> E["Compile Section 1 — max 1 page"]:::grnC
  classDef grn fill:#dcfce7,stroke:#16a34a,color:#14532d
  classDef grnC fill:#16a34a,stroke:#15803d,color:#fff,font-weight:700
```

---

## 🚧 Gate 4: Appendix Completeness

> *Claim review is 🟢. Customer/screenshot verification is 🔴 (requires access to live systems). Sign-off always 🔴.*

```mermaid
flowchart LR
  A["Review claims for data support"]:::grn --> B{"Every claim supported?"}:::yelD
  B -- No --> C["Add evidence OR remove claim"]:::yel
  C --> A
  B -- Yes --> D["Verify customer refs cleared"]:::red
  D --> E["Verify screenshots current"]:::red
  E --> F["Verify sources cited"]:::grn
  F --> G["Memo Owner: SIGN-OFF ✓"]:::redM
  classDef red fill:#fecaca,stroke:#dc2626,color:#7f1d1d
  classDef yel fill:#fef3c7,stroke:#d97706,color:#78350f
  classDef yelD fill:#fbbf24,stroke:#d97706,color:#78350f,font-weight:700
  classDef grn fill:#dcfce7,stroke:#16a34a,color:#14532d
  classDef redM fill:#dc2626,stroke:#b91c1c,color:#fff,font-weight:700
```

---

## ✅ Decision & Approval Block — Section 19

> *Mostly 🔴 — these are executive/board-level decisions. LLM can draft fallback scenarios (🟡) and compile (🟢).*

```mermaid
flowchart LR
  A["Draft decision requested"]:::red --> B["Conditions & non-negotiables"]:::red
  B --> C["Acceptable negotiation range"]:::red
  C --> D["Fallback plan with runway"]:::yel
  D --> E["Escalation triggers"]:::yel
  E --> F["Compile Section 19"]:::grnC
  classDef red fill:#fecaca,stroke:#dc2626,color:#7f1d1d
  classDef yel fill:#fef3c7,stroke:#d97706,color:#78350f
  classDef grnC fill:#16a34a,stroke:#15803d,color:#fff,font-weight:700
```

---

## 🚧 Gate 5: Final Sign-Off & Pre-Submission QC

> *QC checks are a mix: consistency checks 🟢, data freshness 🟡, NDA/legal clearance 🔴. All sign-offs are 🔴.*

```mermaid
flowchart TB
  subgraph QC["Pre-Submission Checklist"]
    direction TB
    Q1["Financials match model"]:::yel --> Q2["Revenue consistent across sections"]:::grn
    Q2 --> Q3["Burn = trailing 3-month actuals"]:::yel
    Q3 --> Q4["UoP ties to hiring plan"]:::grn
    Q4 --> Q5["Comps refreshed within 30 days"]:::yel
    Q5 --> Q6["Customer names NDA-cleared"]:::red
    Q6 --> Q7["Risk disclosures reviewed by Legal"]:::red
    Q7 --> Q8["Page budget enforced"]:::grn
    Q8 --> Q9["Appendix index versioned"]:::grn
  end
  Q9 --> PASS{"All checks pass?"}:::redD
  PASS -- No --> Q1
  PASS -- Yes --> S1x["Financial Data Owner ✓"]:::redM
  S1x --> S2x["Legal / Cap Table Owner ✓"]:::redM
  S2x --> S3x["CEO ✓"]:::redM
  S3x --> S4x["Memo Owner ✓"]:::redM
  S4x --> DONE(["🚀 MEMO CLEARED FOR DISTRIBUTION"]):::redM
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
| 🔴 **LLM Cannot Do** | ~55 | Sign-offs, personnel assignments, deal terms, GL reconciliation, NDA clearance, cap table verification, CEO/board decisions |
| 🟡 **LLM Needs Human Assistance** | ~60 | Draft narratives from data, compute metrics from fed inputs, propose definitions, format financials, build projections from assumptions |
| 🟢 **LLM Can Do** | ~49 | Market research & TAM, comp analysis, scenario modeling, risk frameworks, revenue bridges, section compilation, exec summary, consistency checks |

---

## Usage

**GitHub** — Push this `README.md` for native Mermaid rendering with capability colors.

**Interactive** — Paste charts at [mermaid.live](https://mermaid.live)

**Presentation** — Open `ic_memo_workflow_presentation.html` for the dark-mode scroll-animated version.

---

*IC Production Blueprint v2.0 · LLM Capability Map · Confidential*
