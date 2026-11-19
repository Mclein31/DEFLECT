---
type: decisions
title: Thesis Project — Decision Records
tags:
  - thesis
  - adr
last_updated: 2026-11-15
---

# Thesis Project — Decision Records

> Format: Context, Decision, Consequences. Status is **Accepted** (agreed by the team or set by the adviser) or **Proposed** (recommended by research, still needs team/adviser confirmation).

---

## ADR-001: Paper first, prototype in 4th year

- **Date:** 2026-11-15
- **Status:** Accepted
- **Context:** The team is in the paper-writing stage. The prototype is scheduled for 4th year, 1st semester.
- **Decision:** Current work is research and Chapters 1–3 only. No code, no stack commitment.
- **Consequences:** `ARCHITECTURE.md` stays conceptual. Tech-stack choices are deferred but must be feasible on a student budget.

---

## ADR-002: Snowflake and Databricks are competitors, not components

- **Date:** 2026-11-15
- **Status:** Accepted (set by the adviser)
- **Context:** Early title drafts used Snowflake for tabular data and Databricks for text/graph/OSINT. The adviser named both as the competitors.
- **Decision:** Treat both as existing solutions to benchmark against in the RRL ("existing systems") and in evaluation, not as parts of the proposed system.
- **Consequences:** Titles 2c (hybrid Snowflake + Databricks architecture) and similar framings no longer fit. The thesis needs a clear differentiation from both (see vault `Gap_Analysis_and_Positioning`).

---

## ADR-003: Use synthetic, Philippine-shaped data

- **Date:** 2026-11-15
- **Status:** Proposed
- **Context:** No platform will share real customer data with a student team, and real personal data would bring Data Privacy Act obligations.
- **Decision:** Build a synthetic dataset with Filipino names, phone formats and addresses, injected duplicate accounts and labelled fake-booking behaviour; supplement with public ER/fraud benchmarks.
- **Consequences:** Results are a proof of concept. The paper must explain how the generator mirrors reality and state this as a limitation. Details: vault `Data_Strategy`.

---

## ADR-004: No OSINT on real people

- **Date:** 2026-11-15
- **Status:** Proposed
- **Context:** Several draft titles mention OSINT. Collecting public social-media data on real private individuals raises Data Privacy Act proportionality and consent issues and would need ethics approval. The 2026-11-15 research found NPC Advisory 2026-01 (2026-04-13) stating that public availability is not consent: scraping still needs a lawful basis, privacy notice and PIA, with no research exemption found. Wrong-person matches on common Filipino names add a harm risk.
- **Decision:** Drop OSINT from the core, or restrict it to synthetic "public profile" signals in the simulated dataset.
- **Consequences:** Titles built on OSINT (1a, 1b, 2c, 3b, 4a) should be reworded. Details: vault `Legal_and_Ethical_PH`.

---

## ADR-005: Entity resolution is the core contribution

- **Date:** 2026-11-15
- **Status:** Proposed
- **Context:** The team's own idea is to find accounts with the same or similar info and check if they are used for fake bookings. Generic fraud scoring is crowded; Filipino-aware account linking is not.
- **Decision:** Centre the thesis on entity resolution of customer accounts (with Filipino naming rules), with risk scoring and deflection built on the resulting identity clusters.
- **Consequences:** The title, objectives and evaluation should name and measure the linking step (pair/cluster F1), not just fraud detection.

---

## ADR-006: Design Science Research + CRISP-DM; tree models over end-to-end GNN

- **Date:** 2026-11-15
- **Status:** Proposed
- **Context:** The thesis builds and evaluates an artefact and needs a research design plus a data-mining process. Literature (GADBench) finds tree ensembles with graph-derived features competitive with specialised GNNs for anomaly detection.
- **Decision:** Use Design Science Research (Hevner; Peffers) as the research design, with CRISP-DM for the modelling cycle. Use Routine Activity Theory as the main theoretical lens (Fraud Triangle as support) and IPO for the conceptual framework figure. Use a rules baseline plus gradient boosting (XGBoost/LightGBM) on account, cluster and graph features, explained with SHAP.
- **Consequences:** The prototype stays explainable and feasible for a student team; a GNN can be an optional comparison, not the core. Details: vault `Frameworks_and_Methodology`, `Risk_Scoring_and_ML`.
