---
type: gap-analysis
title: Gap analysis and thesis positioning vs Snowflake/Databricks
tags: [thesis, positioning, gap-analysis, benchmark, philippines]
last_updated: 2026-11-15
---
# Gap analysis

## What platforms do not give out of the box
1. **No finished product.** Closest assets: Databricks card-fraud accelerator (2026-05-19), Snowflake FWA/real-time fraud quickstarts, Zingg/Splink ER. All are card/financial/public-sector examples. [[Databricks]], [[Snowflake]]
2. **Filipino name/identity variation.** Zingg/Splink/ARC are generic fuzzy matchers; Snowflake identity apps are marketing-oriented (coverage of PH data UNVERIFIED). Needs custom handling: nicknames (Jun/Junior/Jr., "Ma." / "Maria"), double surnames, spelling variants, Taglish, informal addresses (barangay/landmark-based), +63/0 phone formats, shared family devices. (Domain reasoning - this is a proposal, not a sourced claim.)
3. **COD-specific risk.** Prank orders cluster in cash payments because no prepayment exists; riders absorb cancellations. News: 16 riders pranked 2020-12 https://coconuts.co/manila/news/how-cruel-16-delivery-men-receive-fake-food-orders-in-manila/ ; Foodpanda offboarded 37 riders for fake bookings (2021) https://www.sunstar.com.ph/davao/opinion/tell-it-to-sunstar-a-note-to-media-from-foodpanda-philippines (snippet-level). Card-fraud models do not capture "ghost address" or rider-collusion patterns.
4. **Merchant/rider protection.** Platform examples score the platform's loss, not rider time/food cost. Proposed bill for rider reimbursement - status UNVERIFIED.
5. **SME cost.** Usage-billed platforms plus ops skills; Databricks Free Edition forbids commercial use; Snowflake trial 30 days. Local SMEs/small platforms unlikely to run either.
6. **Order-time deflection.** Latency numbers exist (Databricks P99 215-392 ms) but the decision policy (challenge / prepay / OTP / block) is left to the user.
7. **PH Data Privacy Act (RA 10173).** Linking accounts = profiling; right to object (Sec. 16(b)) is qualified; NPC Circular 2022-04 requires registration notification of automated decision-making/profiling (secondary sources) https://resourcehub.bakermckenzie.com/en/resources/global-data-and-cyber-handbook/asia-pacific/philippines/topics/artificial-intelligence-profiling-and-automated-decision-making ; IRR https://privacy.gov.ph/wp-content/uploads/2023/06/IRR_RA-10173-as-amended.pdf . Legitimate-interest basis for fraud prevention: UNVERIFIED (check NPC Advisory Opinion 2020-50). Platforms give security tooling, not DPA-compliant design.

## Positioning statement (draft)
"For Philippine food-delivery platforms and merchants that rely on cash-on-delivery, [Title] is a lightweight, explainable duplicate-identity and order-risk scoring framework that links Filipino-pattern customer records, flags likely fake or prank bookings, and recommends order-time deflection, unlike general-purpose data platforms (Databricks, Snowflake) that supply ER and ML building blocks but no COD-aware, PH-localised, privacy-by-design anti-fake-booking solution."

## Differentiators
1. Filipino-aware identity matching (name/nickname/address/phone normalisation) evaluated against generic Zingg/Splink baselines.
2. COD-specific risk features and labels (prepaid vs COD, cancellation-at-door, address-reuse, rider-reported).
3. Graded deflection policy (allow / OTP / partial prepay / block) with cost-of-error trade-off including rider/merchant loss.
4. Privacy-by-design for RA 10173: hashed identifiers, explainable reasons, appeal path, data minimisation.
5. Low-cost, runnable on commodity/open-source stack (Postgres/Python) for SMEs.

## Legitimate benchmarking design
- Build one **synthetic** PH food-delivery dataset (customers, orders, devices; injected duplicate/fake-booking rings with Filipino name variants). Do not use real platform data (privacy).
- Baselines: (A) Databricks Customer-ER accelerator (Zingg) + GraphFrames components + MLflow model; (B) Snowflake FWA/real-time fraud quickstart adapted (XGBoost on SPCS); (C) thesis pipeline.
- Metrics: ER precision/recall/F1 on known clusters; fake-order PR-AUC/recall@fixed-FPR; scoring latency p50/p99; cost (DBU/credits + infra per 100k orders); setup effort (person-hours, LOC).
- Caveats: Free Edition/trial limits constrain scale and are non-commercial; vendor latency claims not comparable to student clusters; Zingg AGPL; report configurations transparently.
