---
type: literature-note
title: Theoretical and Conceptual Frameworks, and Development Methodology
tags: [rrl, framework, fraud-triangle, routine-activity-theory, design-science, crisp-dm, ipo]
last_updated: 2026-11-15
---

# Theme 7: Frameworks and methodology

[V] = verified via web search 2026-11-15.

## Theoretical lenses
| Theory | Source | How it maps to fake bookings |
| :-- | :-- | :-- |
| Fraud Triangle (pressure, opportunity, rationalization) | Cressey, D. R. (1953). *Other people's money: A study in the social psychology of embezzlement.* Free Press. [V via secondary sources; the "triangle" label is a later coinage, not Cressey's] | Opportunity is the dominant lever a platform controls: COD with no payment pre-commitment, free account creation, easy re-registration. Pressure/rationalization (pranks, promo hunting) are not observable, a limitation. |
| Fraud Diamond (adds capability) | Wolfe, D. T., & Hermanson, D. R. (2004). The fraud diamond: Considering the four elements of fraud. *The CPA Journal, 74*(12). [V via secondary mentions only; original not opened] | Capability = ability to spin up many accounts/phone numbers/SIMs. Fits multi-account abuse. |
| Routine Activity Theory (motivated offender, suitable target, absence of capable guardian) | Cohen, L. E., & Felson, M. (1979). Social change and crime rate trends: A routine activity approach. *American Sociological Review, 44*(4), 588-608. https://doi.org/10.2307/2094589 [V] | Offender = prankster/abuser; target = rider-fronted COD order/voucher; guardian = the platform's risk controls. Our system strengthens the "guardian". Best fit for a deflection framing. |

Recommended primary lens: Routine Activity Theory (clear mapping to "deflection"), with the Fraud Triangle/Diamond as supporting explanation of why duplicate accounts exist. This is our recommendation, not a published claim.

## Research / design methodology
- **Design Science Research (DSR)**:
  - Hevner, A. R., March, S. T., Park, J., & Ram, S. (2004). Design science in information systems research. *MIS Quarterly, 28*(1), 75-105. https://doi.org/10.2307/25148625 [V; page range differs across BibTeX entries (75-105 vs 75-106), check journal].
  - Peffers, K., Tuunanen, T., Rothenberger, M. A., & Chatterjee, S. (2007). A design science research methodology for information systems research. *Journal of Management Information Systems, 24*(3), 45-77. https://doi.org/10.2753/MIS0742-1222240302 [V]. Six steps: problem identification, objectives, design and development, demonstration, evaluation, communication.
  - Fit: the artifact (anti-fake-booking detector) is a designed IT artifact; paper stage = steps 1-2 (problem + objectives), 4th year = steps 3-5.
- **CRISP-DM**: Wirth, R., & Hipp, J. (2000). CRISP-DM: Towards a standard process model for data mining. *Proceedings of the 4th International Conference on the Practical Applications of Knowledge Discovery and Data Mining*, 29-39. [V citation details; PAKDD-series venue not independently confirmed]. Phases: business understanding, data understanding, preparation, modeling, evaluation, deployment. Fit: the ML pipeline inside the DSR "design and develop" step.
- **IPO (Input-Process-Output) model**: a generic systems-description convention; no specific citation verified. [UNVERIFIED as a source; cite a systems analysis textbook of your choice after checking]. Use it for the conceptual framework figure: Input (account records, orders, device/IP) -> Process (normalize, link, graph, score) -> Output (risk score, linked-account clusters, recommended action).
- **Agile (Scrum)**: no source verified [UNVERIFIED]. If used, cite the Scrum Guide (Schwaber & Sutherland) after checking the current edition.

## Suggested combination
DSR as the overall research methodology (justifies building and evaluating an artifact), CRISP-DM as the data-science process within it, Agile sprints as optional project management for the prototype semester. IPO for the conceptual framework diagram; Routine Activity Theory for the theoretical framework.
