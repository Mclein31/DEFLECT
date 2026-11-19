---
type: competitor-research
title: Snowflake - offerings relevant to anti-fake-booking thesis
tags: [thesis, competitor, snowflake, entity-resolution, fraud]
last_updated: 2026-11-15
---
# Snowflake (competitor / benchmark)

Legend: [P] fetched primary; [S] search snippet only; [3P] third party. UNVERIFIED = not confirmed.

## 1. Fraud references / quickstarts
- **Build Real-Time Fraud Detection Model with Natural Language in Snowflake ML**: synthetic fraud data via prompts (Cortex Code), XGBoost, live REST endpoint on Snowpark Container Services [S]. https://www.snowflake.com/en/developers/guides/build-real-time-fraud-detection-model-with-natural-language-in-snowflake-ml/ (webinar dated 2026-04-14: https://www.snowflake.com/en/webinars/demo/from-prompt-to-production-build-a-real-time-fraud-detection-model-in-snowflake-2026-04-14/)
- **Build FWA (fraud/waste/abuse) detection platform with Cortex AI**: SQL anomaly detection + classification + SQL graph analysis for fraud rings [S; page returned HTTP 403 on direct fetch]. https://www.snowflake.com/en/developers/guides/build-fwa-detection-platform-cortex-ai/
- **Custom model for anomaly detection quickstart** [S]. https://quickstarts.snowflake.com/guide/building_a_custom_model_for_anomaly_detection/index.html
- Neo4j + Snowflake graph (weakly connected components for account linking) - Medium, [3P]. https://medium.com/snowflake/neo4j-and-snowflake-unlocking-the-power-of-graph-databases-to-transform-data-insights-a-true-d6831912bc8f

## 2. ML capability (current names)
- **Snowflake ML** (successor branding of Snowpark ML): Container Runtime, Feature Store (batch + online), ML Jobs, Experiments, Model Registry (+ serving on Snowpark Container Services), ML Observability, Explainability (Shapley), Lineage; "Snowflake CoCo/Cortex Code" agentic ML [P]. https://docs.snowflake.com/en/developer-guide/snowflake-ml/overview
- **ML Functions (Cortex)**: anomaly detection is **time-series only** (timestamp + target; >=12 rows/series; unsupervised or supervised; single/multi-series) [P]. https://docs.snowflake.com/en/user-guide/ml-functions/anomaly-detection . Implication: poorly matched to per-order/per-account duplicate detection; classification function (non-time-series) was Public Preview Apr 2024, current status UNVERIFIED. https://quickstarts.snowflake.com/guide/getting-started-with-snowflake-cortex-ml-forecasting-and-classification
- Dynamic Tables, Snowpipe Streaming, Snowflake Postgres: not fetched - UNVERIFIED details; cite docs.snowflake.com before use.

## 3. Identity / entity resolution
- Marketplace Native Apps for identity resolution exist, mainly **marketing/ad identity** (LiveRamp, Redpoint Identity Studio, Verato, Verisk, FullContact, Adstra; Experian/TransUnion mentioned by Snowflake author, details thin) [S]. https://snowflake.com/blog/liveramp-identity-foundation-with-snowflake-native-apps ; https://www.redpointglobal.com/press-releases/redpoint-launches-identity-studio-on-snowflake-marketplace/ ; https://medium.com/snowflake/snowflake-one-platform-for-first-party-and-partner-identity-resolution-8ed134b56cc5
- **Senzing**: no Snowflake native app found; Senzing is on AWS Marketplace (2026-01-12) [S]. https://resources.senzing.com/reinvent-amazon-marketplace . Quantexa, Amperity on Snowflake: UNVERIFIED.
- Data Clean Rooms: Samba TV example [S]; no food-delivery use verified.
- These apps target consumer-marketing identity graphs (US-centric data assets); coverage of Philippine consumer data is UNVERIFIED and likely poor.

## 4. Customers
| Company | Verdict | Source |
|---|---|---|
| **Deliveroo** | VERIFIED first-party blog (uses Snowflake since ~2017, scalability) | https://www.snowflake.com/en/blog/deliveroo-supports-rapid-growth-seamless-scalability/ |
| **DoorDash** | VERIFIED via partner (Sigma story: 30% more queries, constant Snowflake cost) and Snowflake webinar (customer 360, marketing analytics) | https://www.sigmacomputing.com/customer-stories/doordash-logs-a-30-increase-in-queries-while-keeping-the-snowflake-cost-constant-with-sigma ; https://www.snowflake.com/webinar/building-a-customer-360-with-doordash/ |
| **Instacart** | VERIFIED via Snowflake statement ($28M 2021/2022 spend, cost-optimisation talk) - snippet only | search result, see Sources.md |
| **Rappi** | WEAK: vendor (Rakam) blog only | https://rakam.io/blog/rappi-case-study-real-time-customer-analytics-on-snowflake/ |
| Grab | No evidence found for Snowflake (Grab verified on Databricks) | - |
| Wolt | geospatial case study (not requested) | https://snowflake.com/en/customers/all-customers/case-study/wolt |
No customer story found on fake-order / COD fraud.

## 5. Pricing and access
- Credit-based (warehouse-seconds), storage separate; third-party figures: Standard ~US$2, Enterprise ~US$3, Business Critical ~US$4 per credit in AWS US-East (region-dependent) [3P]. https://cloudchipr.com/blog/snowflake-pricing . Official pricing page returned 403 - treat as UNVERIFIED until checked.
- Free trial: 30 days / US$400 credits, no card [3P+snippet]; verify at signup.
- Student/academic programme: UNVERIFIED.
