---
type: literature-note
title: Privacy-Preserving Linkage, Fairness and Ethics
tags: [rrl, pprl, bloom-filter, fairness, data-privacy-act, philippines]
last_updated: 2026-11-15
---

# Theme 6: Privacy-preserving linkage and ethics

[V] = verified via web search 2026-11-15.

## Privacy-preserving record linkage (PPRL)
- **Schnell, R., Bachteler, T., & Reiher, J. (2009). Privacy-preserving record linkage using Bloom filters. *BMC Medical Informatics and Decision Making, 9*, Article 41.** https://doi.org/10.1186/1472-6947-9-41 (PMC2753305) [V]. Bloom filters on q-grams of identifiers; results comparable to unencrypted matching and better than phonetic encodings. Note: designed for cross-organization linkage; inside a single platform the data is already held, so PPRL is relevant mainly for (a) hashing identifiers in analytics stores and (b) future cross-platform sharing. Known cryptanalytic attacks on Bloom-filter PPRL exist but were not searched here [UNVERIFIED].
- **Vatsalan, D., Christen, P., & Verykios, V. S. (2013). A taxonomy of privacy-preserving record linkage techniques. *Information Systems, 38*(6), 946-969.** https://doi.org/10.1016/j.is.2012.11.005 [V]. 15-dimension taxonomy.

## Fairness in matching and risk scoring
- **Shahbazi, N., et al. (2023). Through the fairness lens: Experimental analysis and evaluation of entity matching. *PVLDB, 16*.** https://www.vldb.org/pvldb/vol16/p3279-shahbazi.pdf (arXiv:2307.02726) [V; title wording and full author list from memory/partial, confirm]. Reliance on proxy attributes such as name can cause unfairness; groups with more similar names face higher false-positive rates. Directly relevant: common Filipino surnames and shared maternal surnames.
- **Nilforoushan et al. (2022). Entity matching with AUC-based fairness. *IEEE BigData 2022*.** https://doi.org/10.1109/BIGDATA55660.2022.10020293 [V existence via search; full title/authors partially retrieved].
- **Mitigating matching biases through score calibration (2024).** arXiv:2411.01685 [V existence; authors not retrieved]. A matcher can look fair at one threshold and biased at another.
- **Evaluating blocking biases in entity matching (2024).** arXiv:2409.16410 [V existence; authors not retrieved]. Bias can enter at blocking stage.
- **Mehrabi, N., Morstatter, F., Saxena, A., Lerman, K., & Galstyan, A. (2021). A survey on bias and fairness in machine learning. *ACM Computing Surveys, 54*(6), Article 115.** https://doi.org/10.1145/3457607 [V].
- **Dal Pozzolo et al. (2018)** and Hitkul et al. (2023): see other notes for scoring/OSINT. The Hitkul et al. social re-identification approach is the sharpest ethics case: linking customers to social-media profiles.

## Philippine legal / data-protection context [PH]
- **Republic Act No. 10173, Data Privacy Act of 2012, and its Implementing Rules and Regulations (2016).** Processing must follow transparency, legitimate purpose and proportionality (confirmed from the IRR via search). IRR: https://privacy.gov.ph/wp-content/uploads/2023/06/IRR_RA-10173-as-amended.pdf [V]. The statutory wording of data minimization (Sec. 11(c): adequate, relevant, suitable, necessary, not excessive) was NOT confirmed verbatim; read the statute before quoting. Automated-decision/profiling rights under the IRR also need a direct read [UNVERIFIED].
- National Privacy Commission site: https://privacy.gov.ph [V existence].

## Synthesis points
1. Names are weak, unequal evidence; fairness work shows name-driven matching can raise false positives for groups with repetitive names. For Filipinos this plausibly includes very common surnames, but no Philippine fairness study was found.
2. Legitimate shared-identity cases to design for: siblings/spouses on one phone or address, boarding houses/dorms, office deliveries, shared family devices, OFW relatives ordering for family.
3. Data minimization suggests: hash or tokenize identifiers, store only derived features, avoid OSINT scraping by default, and keep a human appeal path for blocked or prepay-only users.
