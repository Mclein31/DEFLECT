---
type: synthesis
title: Research Gaps
tags: [rrl, synthesis, research-gap]
last_updated: 2026-11-15
---

# Research Gaps (feeds the "Synthesis" and "Research Gap" sections)

Wording rule: say "to the best of our search" because absence of evidence from a web search is not proof of absence. Re-run searches in Google Scholar, IEEE Xplore, ACM DL, Scopus, and the Philippine E-Journals / HERDIN before submission.

## Gap 1 (strongest): No Filipino-aware identity matching in fraud/fake-account work
ER literature ([[Entity_Resolution]]) covers Fellegi-Sunter, blocking, Jaro-Winkler, Splink, Ditto, but our search found no published matching method or evaluation for Filipino naming conventions (maternal middle names, "Ma.", Jr./III, nicknames, Taglish/Chinese/Spanish romanizations). Only a government description of name structure (DFA) and a generic multi-surname linkage slide deck (Judson, 2013) were found. Fairness work (Shahbazi et al., 2023) shows name proxies inflate false positives for groups with similar names, which plausibly affects very common Filipino surnames. Contribution: a Filipino-name normalization and similarity scheme tested for duplicate-account detection.

## Gap 2: Duplicate-account linkage is studied as ER or as Sybil detection, not as "linked accounts -> abuse intent" in COD delivery
Sybil work (SybilRank, Integro, Xiao et al.) needs social graphs or assumes malicious intent; ER work treats matching as the end goal. Delivery fraud systems (DeFraudNet, VPGNN, TRUST, Grab GraphBEAN) use shared device/address links inside proprietary pipelines. Nobody in our retrieved set separates (a) accounts that are merely linked (family, roommates, personal+work) from (b) accounts used for fake bookings, prank COD orders, and promo abuse, and checks whether linked accounts are still active. Contribution: a two-stage design (link, then classify abuse) with an explicit "legitimate shared identity" class.

## Gap 3: No open, reproducible, COD-focused food-delivery fraud study; none Philippine
Industry results (Meesho TRUST, Grab, DeFraudNet, Flipkart RTO) are proprietary and not Philippine, except Grab (SEA, not PH-specific). Philippine evidence of the problem is journalistic (Inquirer 2020/2021 on rider-borne fake COD bookings; DTI advice to pay online). We found no peer-reviewed quantification. Contribution: a documented problem definition, feature design, and (in the prototype stage) synthetic or de-identified-data evaluation for the Philippine COD setting. Note: data access will be the main limit.

## Gap 4: Deflection decisioning and its customer cost are not evaluated academically
Industry docs describe routing risky COD orders to prepayment or blocking promos (Cashfree RTO, Meesho "intercept before placement", Grab action pipeline), but we found no academic evaluation of the trade-off between rider/merchant loss prevented and legitimate-customer friction (false positives, churn). Dal Pozzolo et al. (2018) supports precision@k and investigator feedback in card fraud, not in delivery. Contribution: cost-aware thresholding with action tiers (allow / challenge / prepay / manual review) and an explicit false-positive cost model.

## Gap 5: Ethics and Data Privacy Act compliance of OSINT enrichment and cross-account linking
Hitkul et al. (2023) shows social-media re-identification improves RTO prediction (+3.1% precision, +19.9% recall per the paper's reported figures; verify), but fairness and privacy implications are rarely studied in delivery. PPRL (Schnell et al., 2009; Vatsalan et al., 2013) targets cross-organization linkage. Under RA 10173 (transparency, legitimate purpose, proportionality) intrusive enrichment may be hard to justify. Contribution: a privacy-by-design pipeline (hashed identifiers, derived features only, human appeal path) and an explicit decision on whether OSINT is in scope.

## Lesser gaps / design-justification points
- Tree-based models with graph-derived features are competitive with GNNs (GADBench), supporting a lighter, explainable (SHAP) prototype instead of an end-to-end GNN.
- Multimodal tabular + text signals (e.g., rider notes, address strings, order remarks): we found no verified delivery-specific multimodal fraud paper; treat as exploratory.
- Label scarcity: DeFraudNet's weak supervision and Grab's unsupervised GraphBEAN show two routes; the thesis must state its label source (rider-reported no-shows, refused COD, RTO).

## Suggested one-paragraph synthesis (draft)
Prior work provides mature techniques for record linkage and for graph- and boosting-based fraud detection, and large platforms report deployed systems for COD return-to-origin and promotion abuse. However, these systems are proprietary, built on non-Philippine data, and do not address the naming conventions of Filipino customers. Sybil-detection research depends on social graphs, while ER research stops at deciding whether two records match. Few studies connect linked duplicate accounts to abuse intent, evaluate the customer cost of deflecting risky COD orders, or consider privacy and fairness obligations under the Philippine Data Privacy Act. This study addresses these gaps by [fill in: design of a Filipino-aware, privacy-conscious duplicate-account linkage and risk-scoring approach for COD food delivery].
