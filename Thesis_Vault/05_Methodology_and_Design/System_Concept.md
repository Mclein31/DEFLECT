---
type: design
title: System Concept and Conceptual Framework (Draft)
tags:
  - thesis
  - chapter-3
  - design
last_updated: 2026-11-15
---

# System Concept and Conceptual Framework (Draft)

How the proposed system works, written for the paper. The engineering view (components, evaluation, stack) is in the project brain's `.brain/ARCHITECTURE.md`. Back to [[MOC_Thesis]].

## Conceptual framework (Input–Process–Output)

| Input | Process | Output |
| :--- | :--- | :--- |
| Customer accounts (name, phone, email, address, device ID, sign-up date) | 1. Standardise records with Filipino naming rules | Identity clusters (groups of linked accounts) with match confidence |
| Order history (status, payment method, cancellations, failed COD, vouchers) | 2. Block and match candidate account pairs (entity resolution) | Per-order risk score (0–100) with top reasons |
| Rider / merchant reports of no-shows and prank orders | 3. Build an account-link graph and cluster it | Deflection decision: allow, OTP, prepay, review, block |
| New incoming order | 4. Compute account- and cluster-level behaviour features | Analyst dashboard and audit log |
| | 5. Score risk (rules + ML) and choose a proportionate action | Evaluation results vs Snowflake / Databricks baselines |
| | 6. Learn from outcomes (feedback loop) | |

## Worked example

1. *Ma. Cristina Dela Cruz* (account A) is banned after three refused COD orders.
2. *Maria Kristina de la Cruz* (account B) signs up a week later with a phone that differs by one digit, the same barangay and the same device.
3. Standardisation turns "Ma." into "Maria" and "Dela Cruz"/"de la Cruz" into one surname key. Phonetic encoding makes Cristina/Kristina collide.
4. The matcher scores A–B as a likely match; the graph puts them in one identity cluster.
5. B's first order is COD, ₱1,800, late at night. The cluster's history (banned member, three failed CODs) drives the risk score to 87.
6. The decision engine requires prepayment and explains why. B can still order by paying online, so a legitimate relative is not locked out.

## Why identity clusters, not single accounts

Fraud scoring per account resets every time a fraudster opens a new account. Scoring the **cluster** carries history across accounts, which is the gap the team's original idea targets.

## Fairness guardrails (to design in)

- Families share surnames, addresses and sometimes phones. Shared address alone must not link accounts; require several independent signals.
- Prefer soft actions (OTP, prepayment) over blocking.
- Show reasons and allow appeal / manual review.
- Measure false positives on synthetic "legitimate household" clusters.
