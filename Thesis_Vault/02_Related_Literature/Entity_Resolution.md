---
type: literature-note
title: Entity Resolution, Record Linkage and Deduplication
tags: [rrl, entity-resolution, record-linkage, name-matching, filipino-names]
last_updated: 2026-11-15
---

# Theme 1: Entity Resolution / Record Linkage

Legend: [V] = existence and bibliographic details checked via web search on 2026-11-15. [UNVERIFIED] = could not confirm; do not cite until checked. [PH/SEA] = Philippine or Southeast Asian relevance.

## Foundations
- **Fellegi and Sunter (1969)** [V]. Formal probabilistic theory of record linkage: per-field agreement weights (m- and u-probabilities) and two thresholds that split pairs into match / possible match / non-match. Known weakness: conditional-independence assumption is often violated (e.g., address fields correlated). Use as the theoretical anchor for the "similar identity" scoring.
  - Fellegi, I. P., & Sunter, A. B. (1969). A theory for record linkage. *Journal of the American Statistical Association, 64*(328), 1183-1210. https://doi.org/10.2307/2286061
  - Note: a DOI of the form 10.1080/01621459.1969.10501049 was NOT confirmed; use the JSTOR DOI above.
- **Winkler (1990)** [V, venue partly unverified]. Jaro-Winkler string comparator within the Fellegi-Sunter model. Full text: https://www.stat.cmu.edu/NCRN/PUBLIC/RLClassFiles/HW/Winkler1990.pdf . The venue (ASA Section on Survey Research Methods proceedings) was not confirmed; cite as "U.S. Census Bureau / ASA proceedings" only after checking.
- **Christen (2012)** [V]. Standard textbook: indexing/blocking, comparison, classification, evaluation. Christen, P. (2012). *Data matching: Concepts and techniques for record linkage, entity resolution, and duplicate detection*. Springer. https://doi.org/10.1007/978-3-642-31164-2
- **Papadakis et al. (2020)** [V]. Survey of blocking and filtering to avoid O(n^2) comparisons. Papadakis, G., Skoutas, D., Thanos, E., & Palpanas, T. (2020). Blocking and filtering techniques for entity resolution: A survey. *ACM Computing Surveys, 53*(2), Article 31. https://doi.org/10.1145/3377455 (preprint arXiv:1905.06167).

## String similarity and phonetic matching
- **Christen (2006)** [V existence; exact venue UNVERIFIED]. Comparison of personal-name matching techniques on four name datasets; found pattern-matching (e.g., Jaro-Winkler) generally beats phonetic encodings, no technique dominates. Slides: https://cs.anu.edu.au/people/Peter.Christen/publications/mcd2006-slides.pdf . Check whether it is the ANU technical report TR-CS-06-02 or the ICDM Workshops 2006 paper before citing.
- Original sources for Levenshtein (1966), Jaro (1989), Soundex (Russell, 1918/1922 patents) and Double Metaphone (Philips, 2000, *C/C++ Users Journal*) were **not** verified in this session: [UNVERIFIED]. Recommend citing Christen (2012) as the secondary source for all of them.
- Practical takeaway: Soundex/Metaphone are English-centric; for Taglish/Spanish-derived Filipino spellings (e.g., "Jhon/John", "Cristine/Christine", "Ma./Maria") character-level comparators (Jaro-Winkler, Levenshtein) plus a Philippine-specific normalization table (nickname and honorific dictionary) are more defensible. This is an inference, not a published finding.

## Probabilistic and learning-based tools
- **Splink** [V]. Linacre, R., Lindsay, S., Manassis, T., Slade, Z., & Hepworth, T. (2022). Splink: Free software for probabilistic record linkage at scale. *International Journal of Population Data Science, 7*(3). https://doi.org/10.23889/ijpds.v7i3.1794 . Unsupervised EM-estimated Fellegi-Sunter, DuckDB/Spark backends, 100M+ records. Caveat: weaker when fields are highly correlated (city + postal code), which applies to addresses.
- **Dedupe** [V, software docs only; no peer-reviewed paper found]. Active-learning fuzzy matching library for structured data. https://dedupe.readthedocs.io/en/stable/API-documentation.html
- **Zingg** [V, software docs only]. Open-source Spark ML entity resolution (AGPL-3.0, created by Sonal Goyal), five-phase workflow findTrainingData / label / train / match / link. https://github.com/zinggAI/zingg . Databricks publishes a solution accelerator for it (the vendor-comparison agent covers that angle).
- **DeepMatcher** [V]. Mudgal, S., et al. (2018). Deep learning for entity matching: A design space exploration. *SIGMOD '18*. https://doi.org/10.1145/3183713.3196926 . Finding: deep learning does not beat classical methods on structured data but clearly wins on textual/dirty data.
- **Ditto** [V]. Li, Y., Li, J., Suhara, Y., Doan, A., & Tan, W.-C. (2020/2021). Deep entity matching with pre-trained language models. *PVLDB, 14*(1), 50-60. https://doi.org/10.14778/3421424.3421431 (arXiv:2004.00584). Transformer-based matcher; 96.5% F1 on a 789K x 412K company matching task. Needs labelled pairs, which the thesis will not have at paper stage.

## Filipino / Southeast Asian name matching
- **Finding: no published Filipino-specific name-matching or record-linkage algorithm was found** in this search (see [[Research_Gaps]]). This is itself a usable gap statement, worded carefully as "to the best of our search".
- **Name structure (primary, government)** [V, PH]: Philippine DFA certification describing that the middle name is the mother's unmarried surname and the last name is the father's; married women may hyphenate maiden and husband surnames. https://newyorkpcg.dfa.gov.ph/images/2023uploads/FORMS/LEGAL/Certification-Philippine-Recording-of-names_1600258815.pdf
- **Linkage consequence**: middle names are often reduced to initials or dropped in other systems and in app sign-ups, so a middle name conflict should be a weak (not disqualifying) negative signal; shared maternal surname + same last name suggests siblings/relatives, a legitimate-household risk (see [[Privacy_and_Ethics]]).
- **Hispanic/Asian naming conventions in linkage** [V, partly]: Judson (2013), FCSM research conference slides on linking with multi-surname naming conventions: https://www.fcsm.gov/assets/files/docs/J1-Judson-FCSM-2013.pdf . Author given name only as "Judson"; full author list and title not confirmed.
- Challenges to list in the paper (our synthesis, no single source): multiple given names ("Maria Cristina"), "Ma."/"Ma" for Maria, suffixes (Jr., III), nicknames (Jun-Jun, Bong, Ate/Kuya as honorifics), Spanish-derived and Chinese-derived surnames with variant romanization (Tan/Tang, Co/Ko), Taglish/phonetic spelling, and extremely common surnames (Santos, Reyes, Cruz, Dela Cruz/Delacruz). Frame these as hypotheses to test in the prototype.
- Related items found but NOT usable as sources: an unnamed older Hawaii study on name-matching across ethnic groups (mentioned in a search summary; title/authors not retrieved) [UNVERIFIED].
