---
type: architecture
title: Thesis Project — Conceptual Architecture
tags:
  - thesis
  - architecture
  - planned
last_updated: 2026-11-15
---

# Thesis Project — Conceptual Architecture

> **Status: conceptual, not built.** This is the working design for Chapter 3 (methodology / system design). The prototype is scheduled for 4th year, 1st semester. Change it freely until then, and record real decisions in [DECISIONS.md](DECISIONS.md).

## 1. Pipeline overview

```text
 Platform data (synthetic for the thesis)
 customers · orders · devices · addresses · vouchers · rider reports
        │
        ▼
 [1] Ingest & standardise ── clean names, phones (+639XX), emails, addresses
        │
        ▼
 [2] Blocking ───────────── cheap candidate pairs (same phone prefix, phonetic surname,
        │                    same barangay, same device, same email local-part …)
        ▼
 [3] Pairwise matching ──── similarity features (Jaro–Winkler, phonetic, token sort,
        │                    exact phone/device/email) → match probability
        ▼
 [4] Identity clustering ── graph of accounts linked by matches + shared identifiers
        │                    → connected components / communities = "identity clusters"
        ▼
 [5] Activity & behaviour ─ per account and per cluster: active status, order velocity,
        │                    COD failure / cancellation rate, no-show reports, voucher use,
        │                    new-account age, address drift
        ▼
 [6] Risk scoring ───────── rules + ML model → order-time risk score with reasons
        │
        ▼
 [7] Decision (deflection) ─ allow │ OTP challenge │ require prepayment │ manual review │ block
        │
        ▼
 [8] Feedback loop ──────── outcomes (delivered / fake / disputed) relabel data, retrain
```

Two speeds:

- **Batch (offline):** steps 1–5 rebuild identity clusters and behaviour features on a schedule.
- **Online (order time):** step 6–7 score a new order in well under a second, using precomputed cluster features plus the order's own signals.

## 2. Components (planned)

| # | Component | Purpose | Candidate techniques |
| :--- | :--- | :--- | :--- |
| 1 | Standardiser | Make records comparable | Filipino-aware name rules (Ma. → Maria, Jr./III, middle names, nicknames), phone normalisation to E.164, address tokenisation to barangay/city |
| 2 | Blocker | Avoid comparing every pair (n² problem) | Phonetic keys, sorted neighbourhood, LSH/MinHash |
| 3 | Matcher | Decide "same person?" | Fellegi–Sunter (e.g. Splink), or supervised classifier on similarity features |
| 4 | Cluster builder | Group linked accounts | Graph connected components, community detection |
| 5 | Feature builder | Describe behaviour | Aggregates per account and cluster |
| 6 | Risk scorer | Fake-booking likelihood | Rule baseline + gradient boosting (XGBoost/LightGBM); SHAP for reasons |
| 7 | Decision engine | Proportionate response | Score thresholds mapped to actions; cost-based tuning |
| 8 | Review console | Human-in-the-loop | Analyst view of cluster, evidence and decision |

## 3. Evaluation plan (draft)

- **Entity resolution:** precision, recall, F1 of matched pairs and clusters on labelled synthetic data.
- **Fake-booking detection:** PR-AUC, recall at a fixed false-positive rate, precision@k (imbalanced data, so not plain accuracy).
- **Operational:** scoring latency, cost per 10k orders.
- **Benchmark vs competitors:** run the same synthetic dataset through a Databricks accelerator / Snowflake quickstart equivalent and compare (see vault: [Gap_Analysis_and_Positioning](../Thesis_Vault/03_Competitors_Snowflake_Databricks/Gap_Analysis_and_Positioning.md)).
- **Fairness:** false-positive rate on legitimate users who share names or households.

## 4. Tech stack

Not chosen. Decide in 4th year once the methodology chapter is approved. Constraints: student budget, free tiers, reproducibility for the panel.
