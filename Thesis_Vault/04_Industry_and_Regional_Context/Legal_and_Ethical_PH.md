---
type: research-note
title: Legal and Ethical Constraints (Philippines) - Duplicate-Account Linking, Risk Scoring, OSINT
tags: [thesis, legal, ethics, data-privacy-act, npc, osint, scraping, philippines]
last_updated: 2026-11-15
---

# Legal and Ethical Assessment (Philippines)

> Not legal advice. Statements marked **[PRIMARY]** were read from the official/primary text in this session; **[SECONDARY]** come from law-firm or news summaries; **UNVERIFIED** means not checked. Have the thesis adviser/ethics board confirm before relying on any of this.

## 1. Data Privacy Act of 2012 (RA 10173)
Source read: [lawphil.net RA 10173](https://lawphil.net/statutes/repacts/ra2012/ra_10173_2012.html) [PRIMARY, via fetch summary].
- **Sec. 11** principles: transparency, legitimate purpose, proportionality; data adequate/not excessive; retained no longer than necessary.
- **Sec. 12(f)**: processing allowed when "necessary for the purposes of the legitimate interests pursued by the personal information controller" unless overridden by data-subject fundamental rights. Fraud prevention by a platform over its own customer data is a plausible legitimate interest (the statute does not name fraud prevention explicitly - that application is the author's inference).
- **Sec. 13**: sensitive personal information (e.g., government IDs, health, etc.) is prohibited unless an exception applies. Legitimate interest **cannot** be used for sensitive/privileged information (see Circular 2023-07 below). Avoid SPI in the thesis design (no government ID numbers).
- **Sec. 16** rights: be informed, access (incl. info on automated processes "where the data will or likely to be made as the sole basis for any decision that would significantly affect" the data subject, Sec. 16(c)(6)), correction, blocking/erasure, damages. The Act itself does not use the word "profiling".
- **Sec. 4(d)**: personal information processed for journalistic, artistic, literary or **research** purposes is outside the Act's scope (to the extent provided in the Act). Do **not** rely on this for scraping real people: the NPC scraping advisory (below) says DPA still applies; scope of the research carve-out for a student project is UNVERIFIED.
- Penalties Sec. 25-32 (unauthorized processing, processing for unauthorized purposes, unauthorized access, malicious/unauthorized disclosure) - criminal liability.

## 2. NPC issuances
| Issuance | Date | Relevance | Status |
|---|---|---|---|
| **NPC Circular 2023-07, Guidelines on Legitimate Interest** | 13 Dec 2023; effective 15 days after publication; 90-day transition for Sec. 8(B) | Three-part test: **purpose** (specific, lawful, declared to data subject), **necessity** (adequate, relevant, not excessive; lawful means; "cannot violate any law"), **balancing** (impact on subject, mitigating measures e.g. privacy-enhancing tech, alternatives, reasonable expectation). Must document a legitimate interest assessment (LIA). Cannot be used for sensitive PI. | [PRIMARY: PDF](https://newsbytes.ph/wp-content/uploads/2024/08/NPC-Circular-No.-2023-07_Guidelines-on-Legitimate-Interest_13-December-2023.pdf) (mirror of NPC doc) |
| **NPC Circular 2022-04** (registration of DPOs/data processing systems) | effective 11 Jan 2023 (per summary) | Per secondary summary, a data processing system involving automated decision-making or profiling must be registered in all instances. Definition wording differs between draft and final; check final text. | [SECONDARY: Baker McKenzie](https://insightplus.bakermckenzie.com/bm/data-technology/philippines-new-npc-circular-on-registration-of-data-protection-officers-and-data-processing-systems-takes-effect_1); official: [privacy.gov.ph Circular 2022-04](https://privacy.gov.ph/wp-content/uploads/2023/05/Circular-2022-04.pdf) (fetch blocked - UNVERIFIED text) |
| **NPC Advisory 2024-... Guidelines on AI** | 19 Dec 2024 (per URL) | AI systems may involve automated decisions that pose significant risk; extra safeguards. | [PDF](https://privacy.gov.ph/wp-content/uploads/2025/02/Advisory-2024.12.19-Guidelines-on-Artificial-Intelligence-w-SGD.pdf) - advisory number and text UNVERIFIED (not read) |
| **NPC Advisory No. 2026-01, Guidelines on Data Scraping of Publicly Available Personal Data** | **13 Apr 2026** | Covers manual and automated extraction (text, images, user profiles). "Public availability ... does not equate to unrestricted use or implied consent beyond its original purpose." Scraper must have lawful basis (Sec. 12 or 13), specific legitimate purpose, privacy notice/disclosure, data minimisation; a **Privacy Impact Assessment**; stricter obligations for "large-scale" scraping; non-compliance = civil, criminal, administrative liability. Research exemption: **not found in extracted text**. | [PRIMARY-ish: DivinaLaw digest of the advisory](https://www.divinalaw.com/wp-content/uploads/2026/05/NPC-01-NPC-Advisory-No.-2026-01.pdf) (extracted text read; full official text at [privacy.gov.ph SGD_A_1.pdf](https://privacy.gov.ph/wp-content/uploads/2026/04/SGD_A_1.pdf) NOT read); [Baker McKenzie, 8 May 2026](https://www.bakermckenzie.com/en/insight/publications/2026/05/philippines-npc-tightens-rules-on-data-scraping) |
| NPC Circular 2023-04 (consent guidelines) mentioned in secondary source re ADM notice | 2023 | UNVERIFIED | - |
| NPC CCTV/biometrics advisories | - | Not researched; not directly relevant to this design. | UNVERIFIED |

**Implication for the thesis system** (analysis, not a quote):
1. Linking duplicate accounts by name/phone/email/address/device inside the platform's own database is processing personal information; Sec. 12(f) legitimate interest + an LIA is the natural basis. Purpose must be declared in the privacy notice (Circular 2023-07 Sec. 5(C)).
2. Necessity/proportionality: use the minimum attributes (hashed/normalised keys, tokenised device IDs) and keep data no longer than needed.
3. Blocking or forcing prepayment on a customer based on a score is a "significant effect" if solely automated; design with **human review for adverse actions** and an appeal path; include an explanation (reason codes). Registration of ADM/profiling systems with NPC applies to a real deployment, not to a synthetic-data thesis (applicability to a prototype with no real data: UNVERIFIED but logically not triggered).
4. False positives: legitimate duplicates are common (family members sharing a phone/address, office addresses, re-registrations after a SIM change). Grab's own graph posts show a wrongly flagged corporate account. Thesis should measure and discuss false-positive cost.

## 3. Other statutes
- **SIM Registration Act (RA 11934)** [SECONDARY: [Grant Thornton PH](https://www.grantthornton.com.ph/insights/articles-and-updates1/line-of-sight/smishing-no-more-an-overview-of-the-sim-card-registration-act/); [Accralaw](https://accralaw.com/?p=14857); [Manila Bulletin, 10 Oct 2022](https://mb.com.ph/2022/10/10/marcos-signs-sim-registration-act/)]: SIM registration data is confidential and disclosable only under limited exceptions (DPA compliance, court order/subpoena, subscriber's written consent); 10-year retention; penalties PHP 500,000-4,000,000 for breach of confidentiality. Consequence: a delivery platform **cannot** obtain telco SIM-registry data to verify phone ownership; it can only use the phone number the customer gives and verify via OTP. Do not model SIM registry lookups in the thesis. Check lawphil for the text (UNVERIFIED).
- **Internet Transactions Act of 2023 (RA 11967)** [SECONDARY: [Baker McKenzie](https://insightplus.bakermckenzie.com/bm/consumer-goods-retail_1/philippines-implementing-rules-of-the-internet-transactions-act-issued); [NDV Law](https://ndvlaw.com/regulations-affecting-e-marketplaces-online-or-digital-retailers-and-stores-under-the-internet-transactions-act-of-2023/); [DTI](https://dti.gov.ph/news/dti-leads-interagency-signing-internet-transactions-act-guidelines)]: creates the E-Commerce Bureau under DTI; obligations on e-marketplaces/digital platforms; platform subsidiary liability for negligence; IRR is reportedly DAO 24-03 (s. 2024); 18-month transition. Exact IRR dates and the transition end are **UNVERIFIED**. Relevance: platforms have consumer-protection and complaint-handling duties, so a block/prepayment policy must be transparent and contestable; whether the Act directly addresses fake bookings is UNVERIFIED (not found).
- **Cybercrime Prevention Act (RA 10175)** [PRIMARY via lawphil fetch summary: [lawphil](https://lawphil.net/statutes/repacts/ra2012/ra_10175_2012.html)]: Sec. 4(b)(3) computer-related **identity theft** (intentional use/misuse of another person's identifying information without right); Sec. 4(b)(2) computer-related fraud; Sec. 6 raises penalty by one degree for Revised Penal Code crimes committed through ICT. Analysis (not legal opinion): a fake booking that uses a real person's name/address/phone plausibly fits identity theft; one using fully invented details may not, which is why hoax-ordering bills were filed. Actual prosecutorial treatment UNVERIFIED.
- **AFASA (RA 12010, signed July 2024)** [lawphil: [RA 12010](https://lawphil.net/statutes/repacts/ra2024/ra_12010_2024.html); secondary: [NDV Law](https://ndvlaw.com/republic-act-no-12010-the-anti-financial-account-scamming-act-afasa-explained/)]: targets scams on **financial accounts** (money mules, social engineering, unauthorised account use). Fake COD bookings are **not** financial-account scams, so AFASA is **not** directly relevant; at most analogous for the "mule account / borrowed account" concept. Penalty figures differ across secondary sources - do not cite penalties.
- **Consumer Act (RA 7394)**: not researched in this pass - UNVERIFIED.
- **Hoax-ordering bills**: see Problem_Evidence_PH.md; enactment UNVERIFIED.

## 4. OSINT enrichment verdict

**Question:** Should the thesis enrich customer records by scraping social media / the open web to verify identities (e.g., find whether "Juan Dela Cruz, 0917..." has a Facebook profile)?

**Verdict: NO for the thesis. Platform-held data + synthetic data only. Describe OSINT enrichment as a future-work / literature item.**

Reasons:
1. **NPC Advisory No. 2026-01 (13 Apr 2026)** states that public availability does not mean consent or unrestricted use; scrapers need a lawful basis, declared purpose, privacy notice and a PIA; large-scale scraping faces stricter rules. A student cannot satisfy notice-to-data-subject or PIA obligations for strangers' profiles. No research exemption was found in the extracted text (full text UNVERIFIED).
2. **Circular 2023-07**: legitimate interest requires necessity and a balancing test including the data subject's reasonable expectation; people do not reasonably expect a food app to profile them via Facebook. Alternatives (platform-held signals) exist, which weakens necessity.
3. **Platform ToS** of social networks typically prohibit scraping (general knowledge; per-platform check UNVERIFIED).
4. **Accuracy/harm**: name matching to social profiles in a country with very common names (see Data_Strategy.md) yields wrong-person matches; a wrong match leading to a ban/prepayment demand is a real harm.
5. **Ethics review**: any dataset of real people's identity attributes needs ethics clearance and a data protection plan at the university; avoid it.
6. **Commercial practice differs**: vendors like SEON run footprint checks under their own data agreements; replicating that by scraping is not equivalent.

**Safe boundaries (recommended to put in the thesis scope/limitations):**
- Inputs limited to attributes the platform already holds from its own customers (name, phone, email, delivery address, device ID, order history) - **in the thesis, entirely synthetic**.
- No scraping, no lookups on real people, no use of leaked datasets, no real phone numbers (use clearly fake/reserved patterns or randomised numbers; never test numbers on real services).
- If enrichment is discussed, model it as a **simulated, binary "enrichment signal"** (e.g., synthetic "email-registered-on-N-services" feature) clearly labelled synthetic.
- Document a mock Legitimate Interest Assessment (purpose/necessity/balancing per Circular 2023-07) and mock PIA as thesis appendices - shows legal awareness.
- Human-in-the-loop for adverse actions; reason codes; appeal path; measure false-positive rate by segment (shared-household simulation).
- Data minimisation: hash/tokenise identifiers in the pipeline; avoid sensitive PI (government IDs).
