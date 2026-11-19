---
type: competitor-research
title: Databricks - offerings relevant to anti-fake-booking thesis
tags: [thesis, competitor, databricks, entity-resolution, fraud]
last_updated: 2026-11-15
---
# Databricks (competitor / benchmark)

Source-quality legend: [P] primary vendor page fetched; [S] search-result snippet only (not opened); [3P] third party. UNVERIFIED = not confirmed.

## 1. Fraud accelerators
- **Real-time credit-card fraud accelerator (Spark Real-Time Mode + Lakebase + Databricks Apps)**, blog dated 2026-05-19 [P]. Kafka -> Spark Real-Time Mode (`transformWithState` per-card velocity state, TTL) -> 5 weighted signals (velocity, geo anomaly, amount deviation, merchant risk, country risk) into a 0-100 explainable score -> approve/flag/block routing; optional RandomForest via MLflow as UDF; features upserted to Lakebase (managed Postgres); Streamlit dashboard. Reported latency: P50 <40 ms, P99 215-392 ms (vendor claim). https://databricks.com/blog/how-build-real-time-fraud-detection-using-spark-real-time-mode-and-lakebase
  - Relevance: the routing pattern (approve / review / block) maps directly onto the thesis "deflection" idea (allow / challenge / force prepayment / block). It is card-transaction oriented, not COD or identity-duplication oriented.
- No Databricks accelerator found that combines entity resolution + fraud for food delivery [S, absence of evidence]. Mark "no such accelerator found" as UNVERIFIED-negative.

## 2. Entity resolution / record linkage
| Asset | What | Status / notes | Source |
|---|---|---|---|
| Customer Entity Resolution accelerator (Zingg) | Fuzzy matching of person records (name, address, phone); blocking; 2 phases: label pairs -> train, then incremental matching. Blog 2022-08-04, ~5M individuals | README: DBR 11.0+, no deprecation notice. Zingg is **AGPL v3** (licence matters for any productisation) | https://github.com/databricks-industry-solutions/customer-er ; https://databricks.com/blog/2022/08/04/new-solution-accelerator-customer-entity-resolution.html |
| ARC "Automated Record Connector" (auto-data-linkage) | Wrapper over Splink (UK MoJ), Hyperopt-tuned, public-sector oriented; announced Apr 2023 | Repo notice recommends using Splink directly; runtime listed DBR 12.2 LTS ML -> likely stale [S] | https://github.com/databricks-industry-solutions/auto-data-linkage ; https://www.databricks.com/blog/improving-public-sector-decision-making-simple-automated-record-linking |
| Partner ER (Reltio notebook on Marketplace; Entrada Golden Lake) | Commercial/partner ER | [S] only | https://community.reltio.com/blogs/ankur-gupta/2026/03/16/unlocking-trusted-entities-at-scale-in-databricks |

Takeaway: Databricks ER = open-source libs (Zingg, Splink) running on Spark; neither is Filipino-name-aware out of the box (see Gap_Analysis).

## 3. Graph
- **GraphFrames**: DataFrame-based graphs on Spark (Java/Python/Scala); connected components / PageRank / motifs. Databricks recommends ML Runtime, which ships an optimised install. https://docs.databricks.com/aws/integrations/graphframes . Third-party note (May 2026): namespace changed to `io.graphframes` from 0.10.0 - UNVERIFIED against release notes.
- Use here: connected components over shared phone/device/address edges = candidate duplicate-account clusters.

## 4. ML / real-time / pipelines / governance (current names)
- **Delta Live Tables -> Lakeflow Spark Declarative Pipelines** (docs page titled "Spark Declarative Pipelines on Lakeflow"; fetch did not state the rename explicitly - rename itself UNVERIFIED from the docs page, though iFood page URL `/spark-declarative-pipelines` supports it). https://docs.databricks.com/aws/en/dlt/
- **Mosaic AI / MLflow / Model Serving**, **Feature Serving / online feature store**, **Unity Catalog** (named in the 2026 fraud blog; Feature Serving details not separately fetched - UNVERIFIED).
- **Lakebase** (managed serverless Postgres) for low-latency feature reads (sub-ms reads is vendor claim).

## 5. Customers (verify-by-source)
| Company | Verdict | Source |
|---|---|---|
| **Grab** | VERIFIED: C360 consumer data platform on Azure Databricks / Delta Lake; ingestion of thousands of signals from weeks -> hours. No fraud use stated. Page undated (c. 2023+). | https://www.databricks.com/customers/grab |
| **iFood** | VERIFIED (listing + vendor URLs): DLT / Spark Declarative Pipelines stories (cost, pipeline maintenance). Content not opened. | https://www.databricks.com/customers/ifood/dlt |
| **Swiggy** | PARTIAL: Data+AI Summit session on AI platform (Spark, Delta, Unity Catalog) - [S] | https://www.databricks.com/dataaisummit/session/how-open-scalable-and-secure-data-platform-powering-quick-commerce |
| DoorDash | UNVERIFIED (only passing mention) | - |
| Zomato, Deliveroo, Rappi, Instacart, Gojek | No Databricks evidence found - UNVERIFIED | - |

No found customer story is specifically about fake bookings / COD fraud.

## 6. Pricing and access
- Pay-as-you-go, per-second billing, billed in **DBUs** (compute) + cloud infra; committed-use discounts via sales; list-price table and calculator are separate pages (rates not retrieved). https://www.databricks.com/product/pricing
- **Free Edition** (replaced Community Edition in 2025): serverless only, no R/Scala, 1 SQL warehouse 2X-Small, 5 concurrent job tasks, **no online tables, no clean rooms**, 3 apps (auto-stop 24 h), 1 Lakebase project, non-commercial, no SLA, daily quota. https://docs.databricks.com/aws/en/getting-started/free-edition-limitations
- Free trial with credits exists (amount not retrieved). Academic-email full access claim is community-post only - UNVERIFIED. https://community.databricks.com/t5/databricks-university-alliance/guide-and-best-practices-moving-from-community-edition-to-free/ta-p/129308
