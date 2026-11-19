---
type: planning
title: Problem Statement and Objectives (Draft)
tags:
  - thesis
  - chapter-1
  - draft
last_updated: 2026-11-15
---

# Problem Statement and Objectives (Draft)

Working draft for Chapter 1. Wording is a starting point for the team, not final. Back to [[MOC_Thesis]].

## The problem in one paragraph

Food delivery platforms in the Philippines rely heavily on Cash-on-Delivery. When a customer places a fake or prank COD order, the rider (who may have paid the merchant upfront) and the merchant absorb the loss. Platforms ban abusive accounts, but the same person can return with a new account under a slightly different name, a second SIM or a family member's details. Platforms rarely link these near-duplicate accounts to one person, so bans and limits are easy to evade. General data platforms such as Snowflake and Databricks provide building blocks for fraud detection and entity resolution, but they are not ready-made, locally tuned solutions for COD fake bookings. Evidence and statistics: [[Problem_Evidence_PH]].

## General problem (draft)

How can a food delivery platform identify customer accounts that belong to the same person or coordinated group, and use that linkage to detect and deflect fake bookings before dispatch?

## Specific problems (draft)

1. How can customer records with Filipino naming patterns (multiple given names, maternal middle names, "Ma.", suffixes, nicknames, spelling variants) be standardised and matched accurately?
2. Which identity signals (name, phone, email, address, device) and behavioural signals (cancellations, failed COD, order velocity, voucher use, account age) best indicate that linked accounts are used for fake bookings?
3. How accurately can the proposed system (a) resolve duplicate accounts and (b) detect fake bookings, measured by precision, recall, F1 and PR-AUC?
4. How does the proposed system compare with equivalent pipelines built on Snowflake and Databricks in accuracy, scoring latency and cost?
5. How can the system act on risk proportionately (OTP, prepayment, review, block) while keeping false positives on legitimate users low and complying with the Data Privacy Act of 2012?

## General objective (draft)

To design, develop and evaluate an identity-linked risk scoring system that detects and deflects fake bookings on Cash-on-Delivery food delivery platforms.

## Specific objectives (draft)

1. To develop a Filipino-aware record standardisation and entity-resolution module that groups customer accounts into identity clusters.
2. To engineer account- and cluster-level behavioural features and build a fake-booking risk model.
3. To implement a decision engine that maps risk scores to proportionate deflection actions with human-readable reasons.
4. To evaluate the system's matching and detection performance on a labelled synthetic dataset.
5. To benchmark the system against Snowflake- and Databricks-based equivalents on accuracy, latency and cost.
6. To evaluate software quality using ISO/IEC 25010 (to confirm with adviser).

## Scope (draft)

- Customer-side fake bookings on food delivery platforms; rider-side and merchant-side fraud are out of scope unless the adviser asks.
- Synthetic data modelled on Philippine naming, phone and address formats; no real customer data and no scraping of real people.
- Prototype as a web-based analyst console plus a scoring API.

## Delimitations (draft)

- No live integration with Foodpanda, GrabFood or any real platform.
- No collection of public social-media data on real individuals (see [[Legal_and_Ethical_PH]]).
- No payment processing; "require prepayment" is simulated.

## Significance (who benefits)

- **Riders** — fewer unpaid COD orders.
- **Merchants** — less food wasted on prank orders.
- **Platforms** — ban evasion and promo abuse become harder; a cheaper, locally tuned alternative to general platforms.
- **Legitimate customers** — proportionate checks instead of blanket COD bans.
- **Future researchers** — a Filipino-name entity-resolution approach and a synthetic benchmark dataset.
