---
type: map-of-content
title: Thesis — Map of Content
tags:
  - moc
  - thesis
last_updated: 2026-11-15
---

# Thesis — Map of Content

**Topic:** detecting and deflecting fake bookings on Cash-on-Delivery food delivery platforms by linking duplicate/similar customer accounts (entity resolution) and scoring order risk. **Stage:** paper writing (Chapters 1–3); prototype in 4th year, 1st semester. **Competitors (adviser):** Snowflake, Databricks.

Operational state, decisions and tasks live in the project brain: `thesis_project/.brain/` (start with `PROJECT_CONTEXT.md`).

## Research digest (2026-11-15 first pass)

**Competitors.** Neither Snowflake nor Databricks sells an anti-fake-booking or food-delivery fraud product, and no customer story about fake orders or COD fraud was found at either. They provide building blocks:
- **Databricks:** a real-time card-fraud accelerator (2026-05-19) that routes transactions to approve/flag/block, with claimed P99 of 215–392 ms; Zingg (AGPL) and Splink for entity resolution; GraphFrames for graphs. Verified food-delivery customers include Grab and iFood.
- **Snowflake:** fraud quickstarts (XGBoost on Snowpark Container Services, a Cortex AI fraud/waste/abuse example) and marketing-oriented identity Native Apps. Verified food-delivery customers include Deliveroo and DoorDash.

→ [[Gap_Analysis_and_Positioning]]

**Literature.** Entity resolution and fraud ML are mature, but the search found:
- no Filipino-aware name matching;
- no work separating "linked but legitimate" accounts (family, roommates) from "linked and abusive" ones in COD delivery;
- no peer-reviewed Philippine fake-booking study;
- no academic evaluation of deflection versus customer friction.

The closest precedents are LinkedIn's cluster-then-classify approach (Xiao et al. 2015), Meesho TRUST, Grab GraphBEAN, DeFraudNet and voucher-abuse GNNs. GADBench supports tree models with graph features over a full GNN. → [[Research_Gaps]]

**Philippines.**
- **Incidents:** documented from 2020 to 2024, including 16 riders sent to one fake address and the PHP 100k COD order to the Robredo office.
- **Platform and Congress responses:** Grab PH capped cash orders at PHP 1,000 (2023). Senate Bill 2302 on hoax ordering passed the Senate in 2022; whether it became law is unverified.
- **No published loss statistic:** none exists, so do not invent one.
- **Legal basis:** account linking can rely on legitimate interest (DPA Sec. 12(f), NPC Circular 2023-07), but only with documented tests and human review.
- **OSINT on real people:** not recommended (NPC Advisory 2026-01).

→ [[Problem_Evidence_PH]], [[Legal_and_Ethical_PH]]

## 01 — Problem & concept
- [[Problem_Statement]] — draft problem, objectives, scope, significance
- [[Concept_Glossary]] — definitions of terms

## 02 — Related literature
- [[RRL_Matrix]] — 55 sources (≈40 fully verified; check the status column before citing)
- [[Research_Gaps]] — five gaps + draft synthesis paragraph
- Themes: [[Entity_Resolution]] · [[Multi_Account_and_Sybil_Detection]] · [[Delivery_and_COD_Fraud]] · [[Graph_Fraud_Detection]] · [[Risk_Scoring_and_ML]] · [[Privacy_and_Ethics]] · [[Frameworks_and_Methodology]]

## 03 — Competitors: Snowflake & Databricks
- [[Databricks]] · [[Snowflake]] · [[Snowflake_vs_Databricks]]
- [[Gap_Analysis_and_Positioning]] — positioning statement, differentiators, benchmark design
- Sources: `03_Competitors_Snowflake_Databricks/Sources.md`

## 04 — Industry & regional context
- [[Problem_Evidence_PH]] · [[Industry_Practices]] · [[Commercial_Vendors]]
- [[Legal_and_Ethical_PH]] · [[Data_Strategy]]
- Sources: `04_Industry_and_Regional_Context/Sources.md`

## 05 — Methodology & design
- [[System_Concept]] — IPO framework, worked example, fairness guardrails

## 06 — Title
- [[Title_Options]] — the 12 drafts reviewed + suggested direction

## 07 — Paper drafting
- [[Chapter_Outline]] — Chapters 1–3 mapped to vault notes

## Before citing anything

Many facts came from search summaries; several sites (Inquirer, Manila Bulletin, an NPC PDF) blocked direct fetching. Open every link yourself, keep only what you confirm, and re-run searches in Google Scholar, IEEE Xplore, ACM DL, Scopus and Philippine E-Journals / HERDIN. Items marked **UNVERIFIED** must not be cited as-is.
