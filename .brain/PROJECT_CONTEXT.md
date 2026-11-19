---
type: project-context
title: Thesis Project — Project Context
tags:
  - thesis
  - fraud-detection
  - entity-resolution
last_updated: 2026-11-15
---

# Thesis Project — Project Context

> **Read this first.** Short, current-state description of the thesis. Research lives in the vault: [Thesis_Vault](../Thesis_Vault/00_Index/MOC_Thesis.md).

## 1. What it is

An undergraduate thesis on **detecting and stopping fake bookings on food delivery platforms** (Foodpanda / GrabFood style, where Cash-on-Delivery is common).

Core idea, in the team's words (still loose, "take it with a grain of salt"):

1. Find all accounts in the platform's customer database with the **same or very similar identity info** (names, plus phone, email, address, device where available).
2. Check whether those linked accounts are **currently active**.
3. Analyse whether the "sibling" accounts are being used for **fake bookings**: prank or bogus COD orders, repeat no-shows, promo/voucher abuse, ban evasion.
4. Score the risk and **deflect** risky orders (allow / challenge with OTP / require prepayment / hold for review / block).

The technical heart is **entity resolution** (finding accounts that belong to the same real person despite spelling differences) combined with **behavioural risk scoring**.

## 2. Stage and timeline

| When | What |
| :--- | :--- |
| 3rd year (now, 2026-11) | Paper writing: Chapters 1–3 (problem, related literature, methodology). No prototype. |
| 4th year, 1st semester | Build and test the prototype. |
| 4th year, 2nd semester | Final defense (assumed; confirm with adviser). |

## 3. Competitors (set by the adviser)

The adviser named **Snowflake** and **Databricks** as the competitors to benchmark against. Both are general-purpose data platforms with fraud and entity-resolution building blocks (accelerators, quickstarts, marketplace partners), not finished anti-fake-booking products. Research: [03_Competitors_Snowflake_Databricks](../Thesis_Vault/03_Competitors_Snowflake_Databricks/).

Earlier title drafts treated Snowflake (tabular) and Databricks (text/graph/OSINT) as *parts* of the system. With the adviser's framing they are *competitors*; see ADR-002.

## 4. Title

Not chosen. Twelve candidates in four framings (ML/multimodal, architecture/big data, applied cybersecurity/COD, acronym) are kept and evaluated in [Title_Options](../Thesis_Vault/06_Title_Options/Title_Options.md).

## 5. Where things are

| Need | Go to |
| :--- | :--- |
| Decisions made so far | [DECISIONS.md](DECISIONS.md) |
| What to do next | [TODO.md](TODO.md) |
| Planned system design (conceptual, not built) | [ARCHITECTURE.md](ARCHITECTURE.md) |
| Open questions, adviser notes, glossary pointers | [NOTES.md](NOTES.md) |
| Research hub | [MOC_Thesis](../Thesis_Vault/00_Index/MOC_Thesis.md) |

## 6. Current status (2026-11-15)

- Brain and vault created; first deep-research pass done by three researcher agents (competitors, related literature, PH industry/legal/data). See CHANGELOG.md. Digest at the top of the vault MOC.
- Key findings:
  - Neither competitor ships an anti-fake-booking product.
  - The strongest research gap is Filipino-aware account linking that separates legitimate shared identities (families) from abusive ones.
  - No published PH loss statistic exists.
  - OSINT on real people is not advisable under the Data Privacy Act.
- Proposed decisions ADR-003 to ADR-006 need team/adviser confirmation.
- Title, team roles, adviser schedule and school paper format not yet recorded.
- Sources: about 15 of the 55 RRL entries are only partly verified. Several news and NPC pages were read through search summaries. Every citation must be checked before it goes in the paper (TODO.md).
