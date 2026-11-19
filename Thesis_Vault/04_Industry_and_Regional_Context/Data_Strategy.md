---
type: research-note
title: Data Strategy for the Thesis (No Real Platform Data)
tags: [thesis, data, synthetic, faker, entity-resolution, febrl, kaggle, sdv]
last_updated: 2026-11-15
---

# Data Strategy

## 1. Verified findings (tested 2026-11-15)
I installed **Faker 40.54.0** in a scratch virtualenv and tested locales:
- `en_PH`, `fil_PH`, `tl_PH` **all exist** (provider folders for address, bank, phone_number, etc.).
- **Phone**: `mobile_number()` returns formats like `0915-382-0747` and `+63995-462-6797`; has `globe_/smart_/sun_mobile_number` and landline methods (note: `phone_number()` is not defined on the PH provider - use `mobile_number()`). Faker's PH phone provider cites Wikipedia numbering lists as source (per source header).
- **Names are NOT realistically Filipino**: sample output was e.g. "Jennifer King", "Valerie Greer", "Carla Mendez", "Cynthia Lopez" - largely Anglo names with some Spanish-origin surnames. fil_PH/tl_PH gave similar results. **Do not claim Faker produces realistic Filipino names.**
- **Addresses** have PH structure (province, 4-digit ZIP, "Village", "Street") but mixes arbitrary city/province pairs (e.g., "El Nido, ... Sorsogon"), so geography is not coherent.
- Sources: [Faker en_PH phone provider source (mirror)](https://tts-labelstudio-audios.ai4bharat.org/env/lib/python3.12/site-packages/faker/providers/phone_number/en_PH/__init__.py); [Faker docs](https://faker.readthedocs.io/) (not fetched); local test.

## 2. PH-realistic generation (build, do not buy)
- **Mobile numbers**: format `09XX XXX XXXX` (11 digits) or `+63 9XX XXX XXXX`. Generate by sampling prefixes (Faker's Globe/Smart/Sun prefix lists, or a curated list) + 7 random digits; apply normalisation tests (0917... vs +63917... vs 63917...). Variants to inject: dash/space formats, missing leading 0, typos, digit transposition. (Prefix assignment from general knowledge; confirm against NTC numbering plan - UNVERIFIED.)
- **Names**: build own lists - common Filipino given names (including nicknames: "Jhon/John", "Ma. Cristina/Maria Cristina", "Jr./III"), surnames with Spanish-origin forms (Dela Cruz / De la Cruz / Delacruz, Santos, Reyes, Garcia) and native ones. Cite PSA/other public frequency data if used (not retrieved - UNVERIFIED; check [PSA](https://psa.gov.ph)). Common names create natural collisions, essential for false-positive testing.
- **Addresses**: structure house/unit + street + barangay + city/municipality + province + ZIP + landmark text ("near 7-Eleven"). Free-text, abbreviation (Brgy., St., Blk/Lot, Subd.), and Taglish variance are the real linkage difficulty. Barangay/city lists: PSA PSGC (UNVERIFIED availability/licence).
- **Emails**: patterns (firstname.lastname + digits, nicknames, Gmail dot/plus aliases).
- **Devices/IPs**: synthetic device_id, shared IPs (households, offices, mobile CGNAT).

## 3. Entity-resolution benchmarks (to validate the linkage component)
| Dataset / tool | What it is | Use | Source |
|---|---|---|---|
| **Febrl** data generator / RLdata | Synthetic person records with injected typos, duplicates, frequency tables; R `RecordLinkage` ships RLdata500/RLdata10000 (50 / 1,000 duplicates) generated from Febrl 0.3 | Sanity-check name/address matching before PH tailoring | [rdrr RLdata](https://rdrr.io/cran/RecordLinkage/man/RLdata.html); [Christen CIKM 2013](https://users.cecs.anu.edu.au/~christen/publications/christen2013cikm.pdf) |
| **North Carolina voters** (with synthetic duplicates via GeCo) | Real US voter records; 5M/10M versions on Leipzig page | Scale tests only; **real people's data** - check licence/terms and ethics; US names, so limited relevance | [Leipzig ER benchmarks](https://dbs.uni-leipzig.de/index.php/research/projects/benchmark-datasets-for-entity-resolution) |
| **Abt-Buy** | Product matching (1081+1092 entities, 1097 matches) | Not person data; only for generic ER method comparison | same Leipzig page |
| **pseudopeople** | Python simulated US population with noise for ER testing | Pipeline/noise-model inspiration; US-centric | [docs](https://pseudopeople.readthedocs.io/en/latest/) (licence UNVERIFIED) |
| Python `recordlinkage`, `splink` | ER libraries | Implementation | whether `recordlinkage` bundles Febrl-style data: UNVERIFIED |

## 4. Fraud datasets (for the scoring/ML part, not the identity part)
- **IEEE-CIS Fraud Detection (Kaggle)**: card-not-present transactions; secondary catalog says non-commercial research only and no redistribution - verify competition rules ([Amazon fraud-dataset-benchmark](https://www.github.com/amazon-science/fraud-dataset-benchmark); [arXiv 2208.14417](https://arxiv.org/html/2208.14417v3)). Lacks PH identity fields and COD.
- **ULB Credit Card Fraud**: DbCL 1.0 per a secondary listing (UNVERIFIED). PCA-anonymised; no identity fields.
- **Amazon Fraud Dataset Benchmark**: curated public fraud datasets bundle ([GitHub](https://www.github.com/amazon-science/fraud-dataset-benchmark)).
- **Food-delivery fake-order dataset**: none found. UNVERIFIED that none exists.
- Use of these is **limited to benchmarking classifiers/class imbalance**; they cannot validate the duplicate-account linkage hypothesis.

## 5. Synthetic tools
- **Faker** (above): scaffolding for fields; needs custom PH providers.
- **SDV**: latest PyPI listing shows Business Source License 1.1 (free for non-commercial; converts to MIT after 4 years), older versions MIT ([PyPI](https://pypi.python.org/pypi/SDV)) - verify LICENSE on GitHub; fine for academic use, but fit only if you have a real seed table, which you do not. Possible use: model order-level numeric/categorical features after you hand-build a seed.
- **Febrl generator / GeCo**: duplicate-with-error injection; Febrl licence UNVERIFIED.

## 6. Recommended strategy
1. **Build a custom agent-based synthetic generator** (Python; Faker for scaffolding + hand-made PH name/address/phone/email lists).
   - Population of N customers (e.g., 100k-1M) in households (shared phone/address/device legitimately).
   - Inject three **fraud archetypes** with labelled ground truth: (a) prank/bogus COD ring (one actor, many accounts, variants of name/phone/email, addresses of third parties, shared device/IP), (b) promo/voucher multi-account farmers, (c) account takeovers or burner-SIM accounts.
   - Inject **benign hard negatives**: families sharing phone/address, roommates, office addresses, SIM recycling, common names, re-registration after phone change.
   - Time dimension: account creation, order bursts, cancellations, activity status ("active/dormant") to mirror the "check if still active" step.
   - Noise model: typos, transpositions, nickname swaps, Taglish address variants, missing fields.
2. **Validate linkage** on Febrl/RLdata first (known ground truth), then on your PH generator; report precision/recall/F1 for linkage separately from fraud classification.
3. **Evaluate scoring** with graph features (connected components, shared-attribute degree) vs baselines (exact-match rules, ML on tabular features); report sensitivity to the synthetic assumptions and publish generator parameters.
4. **Publish the generator + seeds**; state clearly that results show feasibility on synthetic data, not real-world performance. Parameterise fraud prevalence (sweep 0.1%-5%) since no real PH rate is known.
5. **Ethics**: no real PII; no scraping; no real phone numbers; README + mock LIA/PIA.
6. Optional: validate realism of the generator qualitatively with domain experts (e.g., interviews with riders/merchants under ethics approval) - outside this note.
