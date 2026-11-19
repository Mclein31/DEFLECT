---
type: todo
title: Thesis Project — Tasks
tags:
  - thesis
  - todo
last_updated: 2026-11-15
---

# Thesis Project — Tasks

> **Legend:** `[ ]` Not started | `[/]` In progress | `[x]` Done

## Now — paper (3rd year)

### Decide with the team / adviser
- [ ] Answer the open questions in [NOTES.md](NOTES.md) (program, benchmark type, synthetic data, OSINT, scope).
- [ ] Choose a title. Shortlist and notes: vault `06_Title_Options/Title_Options.md`.
- [ ] Confirm ADR-003 (synthetic data), ADR-004 (no OSINT on real people) and ADR-005 (entity resolution as core) with the adviser.
- [ ] Get the school's official thesis format (citation style, chapter headings, ISO/IEC 25010 requirement).

### Chapter 1
- [ ] Draft Background of the Study from `Problem_Evidence_PH`.
- [ ] Finalise Statement of the Problem and Objectives (draft in `01_Problem_and_Concept/Problem_Statement.md`).
- [ ] Scope, Delimitations, Significance, Definition of Terms.

### Chapter 2
- [/] Read and verify every source in `02_Related_Literature/RRL_Matrix.md` (open each link; drop anything marked UNVERIFIED that can't be confirmed).
  - **2026-11-16:** Audited all 55 rows via web access — 33 VERIFIED, 17 CORRECTED, 5 UNVERIFIED (drop/replace #12 and #50; manually open/download #26, #27, #49 in a browser past Cloudflare 403 before citing).
- [ ] Find 5–10 more **local** (Philippine) studies from school libraries / university repositories / Philippine E-Journals.
- [ ] Write the Existing Systems section from the competitor notes (Snowflake, Databricks, commercial vendors).
- [ ] Write the Synthesis and Research Gap from `Research_Gaps.md` + `Gap_Analysis_and_Positioning.md`.
- [ ] Draw the conceptual framework (IPO) from `05_Methodology_and_Design/System_Concept.md`.

### Chapter 3
- [ ] Pick the research design and development methodology.
- [ ] Draw the system architecture and data-flow diagrams.
- [ ] Write the data strategy (synthetic generator design).
- [ ] Define evaluation metrics and the Snowflake/Databricks benchmark protocol.
- [ ] Write ethical considerations (Data Privacy Act compliance).

### Research follow-ups (UNVERIFIED items from the 2026-11-15 pass)
- [ ] Snowflake and Databricks official pricing; Snowflake student programme; Databricks Free Edition limits re-check.
- [ ] Instacart / Rappi as Snowflake customers (sources weak).
- [ ] NPC advisory opinions on legitimate interest for fraud prevention (read the primary text).

## Later — prototype (4th year, 1st semester)
- [ ] Choose the tech stack (student budget, free tiers).
- [ ] Build the synthetic data generator.
- [ ] Build the entity-resolution module and measure pair/cluster F1.
- [ ] Build the risk model and decision engine.
- [ ] Build the analyst console.
- [ ] Run the competitor benchmark.
