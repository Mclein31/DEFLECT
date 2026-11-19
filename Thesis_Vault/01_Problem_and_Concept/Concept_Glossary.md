---
type: reference
title: Concept Glossary
tags:
  - thesis
  - glossary
last_updated: 2026-11-15
---

# Concept Glossary

Plain-language definitions of the terms the paper will use. Back to [[MOC_Thesis]].

| Term | Meaning in this thesis |
| :--- | :--- |
| **Fake booking** | An order placed with no intention of receiving or paying for it: prank orders, bogus COD orders, orders to harass a third party, test orders by fraudsters. |
| **Bogus COD order** | A Cash-on-Delivery order the customer refuses or abandons. The rider or merchant often absorbs the cost because riders may pay the merchant upfront. |
| **Promo / voucher abuse** | Creating many accounts to reuse new-user discounts or referral rewards. |
| **Ban evasion** | Opening a new account after the old one was blocked. |
| **Multi-accounting** | One real person controlling several accounts. Not always malicious (a shared family phone, a work account). |
| **Sybil account** | A fake identity created to gain influence or advantage, from Sybil-attack literature. |
| **Entity resolution (ER)** | Finding records that refer to the same real-world entity. Also called record linkage or deduplication. |
| **Blocking** | Grouping records cheaply so only plausible pairs are compared; avoids comparing every pair. |
| **Fellegi–Sunter model** | Classic probabilistic record-linkage model that weighs how much each field's agreement or disagreement says about a match. |
| **Jaro–Winkler / Levenshtein** | String-similarity measures. Jaro–Winkler favours matching prefixes and suits names. |
| **Phonetic encoding** | Turning a name into a sound code (Soundex, Double Metaphone) so "Jhon" and "John" collide. |
| **Identity cluster** | A group of accounts the system believes belong to one person or one coordinated group. |
| **Active status** | Whether an account placed orders or logged in within a recent window (window to be defined). |
| **Risk score** | A number (e.g. 0–100) estimating how likely an order is to be fake, with the reasons behind it. |
| **Deflection** | A proportionate response to risk: allow, ask for OTP, require prepayment, hold for manual review, or block. |
| **False positive** | A legitimate customer flagged as risky. Costly: lost sales and unfair treatment. |
| **OSINT** | Open-source intelligence: information gathered from public sources. Legally and ethically sensitive when applied to private individuals. |
| **Device fingerprinting** | Identifying a device from its characteristics, used to link accounts on the same phone. |
| **Snowflake** | Cloud data platform (data warehouse/"AI Data Cloud"). Named competitor. |
| **Databricks** | Cloud data and AI platform built on the lakehouse model. Named competitor. |
| **Lakehouse** | Architecture combining a data lake's cheap storage with a warehouse's tables and governance. |
| **Solution accelerator / quickstart** | Vendor-published sample projects (notebooks, guides) that show how to solve a use case on their platform. |
