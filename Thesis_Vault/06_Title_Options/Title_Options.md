---
type: planning
title: Title Options
tags:
  - thesis
  - title
last_updated: 2026-11-15
---

# Title Options

The twelve candidate titles the team drafted, grouped by framing, with notes on fit. **No title is chosen yet.** Back to [[MOC_Thesis]].

## How to read the notes

A title is a promise to the panel: every noun in it has to be built, measured and defended in 4th year. Three things in the drafts carry the most risk:

- **"OSINT"** means collecting public data about real people (social media, search engines). In the Philippines this collides with the Data Privacy Act's proportionality principle, and a student team cannot do it on real people ethically. See [[Legal_and_Ethical_PH]]. If kept, OSINT must be scoped to synthetic or platform-held data.
- **"Real-time"** must be measured (latency target, e.g. under 300 ms per order). Fine if the prototype scores orders online; risky if everything is batch.
- **"Lakehouse / distributed / hybrid cloud"** invites a direct comparison with Snowflake and Databricks, the competitors the adviser named. You would be claiming to out-engineer them on their own ground. Safer: build something *specific* (Filipino-aware identity linking + COD fake-booking scoring) that general platforms do not ship.

The drafts also never mention the team's actual core idea: **linking duplicate or similar accounts** (entity resolution). A title that names it is easier to defend.

## Option 1 — Machine learning & multimodal (CS / Data Science)

| # | Title | Note |
| :- | :--- | :--- |
| 1a | Multimodal Fraud Detection: Fusing Open-Source Intelligence (OSINT) and Transactional Analytics to Deflect Malicious E-Commerce Orders | Heavy on OSINT; "e-commerce" is broader than food delivery. |
| 1b | An OSINT-Enriched Machine Learning Framework for Real-Time Bogus Order Detection and Dynamic Deflection | Two hard promises (OSINT + real-time). |
| 1c | Fusing Tabular Metadata and Unstructured Textual Signals for Early-Stage Malicious Order Classification in Digital Marketplaces | Defensible; no OSINT. Text signals = order notes, addresses, names. |

## Option 2 — System architecture & big data (IT / SE)

| # | Title | Note |
| :- | :--- | :--- |
| 2a | FraudGate: A Distributed Data Lakehouse Architecture for Real-Time Bogus Order Detection and Deflection | Competes head-on with Databricks' lakehouse. |
| 2b | Design and Implementation of a Scalable Lakehouse-Driven Fraud Prevention Engine for Last-Mile E-Commerce Logistics | Same risk; "scalable" must be load-tested. |
| 2c | A Hybrid Cloud Architecture for Real-Time Fraud Deflection: Unifying Structured Transaction Warehousing and Unstructured OSINT Pipelines | Describes Snowflake + Databricks as components, which conflicts with them being competitors. |

## Option 3 — Applied cybersecurity & logistics (IS / regional)

| # | Title | Note |
| :- | :--- | :--- |
| 3a | Mitigating Bogus Orders in Cash-on-Delivery Marketplaces: An Adaptive Risk Scoring and Dynamic Deflection Framework | Strong regional angle (COD is common in PH). Good fit. |
| 3b | Risk-Adaptive Intervention: Deflecting Malicious Consumer Orders in E-Commerce via Behavioral Profiling and OSINT | "Profiling" triggers data-privacy scrutiny; OSINT again. |
| 3c | An Automated Bogus Buyer Identification and Interception System for Digital Consumer Protection | Clear and simple; closest to the duplicate-account idea. |

## Option 4 — Acronym style

| # | Title | Note |
| :- | :--- | :--- |
| 4a | FraudGate: A Risk-Adaptive Intelligent Framework for Detecting and Deflecting Fake Orders Using Multimodal OSINT Signals | Memorable name; OSINT risk. |
| 4b | DEFLECT: Dynamic Evaluation and Fraud-Limiting Engine for Cash-on-Delivery Transactions | Good name, COD focus. The acronym letters should map cleanly. |
| 4c | SENTINEL: Scalable Entity-Normalized Tracking and Intelligence Network for E-Commerce Order Legitimization | "Entity-Normalized" is the only draft that hints at entity resolution. "SENTINEL" is a very common product name. |

## Suggested direction (for discussion with the adviser)

Combine 3a's COD framing with the entity-resolution core, for example:

> **"[Name]: Identity-Linked Risk Scoring for Detecting and Deflecting Fake Bookings in Cash-on-Delivery Food Delivery Platforms"**

> **"Detecting Fake Bookings in Philippine Food Delivery Platforms through Entity Resolution of Duplicate Customer Accounts and Adaptive Risk Scoring"**

These name the real contribution (linking duplicate accounts), the setting (PH food delivery, COD) and the output (risk score + deflection), and leave out OSINT and lakehouse claims. Revisit after reading [[Gap_Analysis_and_Positioning]] and [[Research_Gaps]].
