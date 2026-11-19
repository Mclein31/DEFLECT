---
type: literature-note
title: Fraud in Food Delivery, E-commerce and COD
tags: [rrl, food-delivery, cod, rto, promo-abuse, philippines]
last_updated: 2026-11-15
---

# Theme 3: Fraud in food delivery, e-commerce and COD

[V] = verified via web search 2026-11-15. [PH] = Philippine; [SEA] = Southeast Asian.

## Peer-reviewed / academic
- **Mathew, J., Negi, M., Vijjali, R., & Sathyanarayana, J. (2021). DeFraudNet: An end-to-end weak supervision framework to detect fraud in online food delivery. *ECML-PKDD 2021*, 85-99.** https://doi.org/10.1007/978-3-030-86514-6_6 [V]. Weak labels from customer-service interactions and business rules (Snorkel), autoencoder noise reduction, MLP+LSTM ensemble, GCN customer embeddings on a customer-customer graph for collusion; +16 points recall at fixed precision. Company not named in the source page. Best single match to our domain; shows labels are scarce in food delivery.
- **Wen, Z., Fang, Y., Liu, Y., Guo, Y., & Hao, S. (2023). Voucher abuse detection with prompt-based fine-tuning on graph neural networks. *CIKM 2023 (Applied Research)*.** arXiv:2308.10028 [V]. E-commerce (proprietary data; Lazada per my recollection, NOT confirmed by the source retrieved). Accounts linked by same device or delivery address; VPGNN gives +23.4% online over two deployed models; notes specialized anomaly GNNs (CARE-GNN, GeniePath, AMNet) do not consistently beat vanilla GNNs.
- **Li, S., Han, X., Zhang, Z., Hua, M., Gao, S., Liang, Z., Guo, Y., Chen, X., & Li, D. (2025). PromoGuardian: Detecting promotion abuse fraud with multi-relation fused graph neural networks.** arXiv:2510.12652 [V] (preprint, cs.CR). Meituan; "stocking up" and "cashback abuse"; 93.15% precision; releases the PPA dataset. Possible public dataset to mention for the prototype phase (availability stated in abstract; not checked by us).
- **Hitkul, Abinaya, K., Saha, S., Banerjee, S., Chelliah, M., & Kumaraguru, P. (2023). Social re-identification assisted RTO detection for e-commerce. *Companion Proceedings of The ACM Web Conference 2023 (WWW '23 Companion)*.** https://doi.org/10.1145/3543873.3587620 [V]. Flipkart + IIIT. Matches buyers to social-media profiles to predict Return-to-Origin (RTO); reports gains of 3.1% precision and 19.9% recall (figures from a search snippet of the paper, verify against the PDF). Direct precedent for the "OSINT enrichment" idea, and for its ethics problem.
- **TRUST: Transaction Risk via Unified Sequence and Topology (Meesho). *Proceedings of the AAAI Conference on Artificial Intelligence, 40*, 40147-40156 (2026; IAAI track).** https://doi.org/10.1609/aaai.v40i47.41450 [V; author list not retrieved: UNVERIFIED]. Heterogeneous GNN + Transformer sequence encoders for COD RTO abuse; about 25 ms latency; about +9.6% absolute precision over XGBoost baseline; sub-second pre-placement interception. Strongest "COD + graph + real time" source and a recent one.
- **Scoping review: Food delivery service applications in highly urbanized cities: A scoping review. *International Journal of Computing and Digital Systems, 15*(1), 2024.** https://doi.org/10.12785/ijcds/150159 [V title/DOI/venue; authors not retrieved]. 174 studies, PRISMA 2020. Whether it discusses fake orders was NOT confirmed (an earlier search summary claimed so; do not cite for that claim until the PDF is read).
- **Food delivery apps (FDAs) in Asia: an exploratory study across India and the Philippines. *British Food Journal* (Emerald).** https://doi.org/10.1108/BFJ-01-2020-0074 [V; authors/year not retrieved; one summary gave 2022]. [PH] Context on FDA adoption; not fraud-specific.

## Industry engineering (cite as grey literature)
- **Fathony, R., Ng, J., & Chen, J. (2023, Aug 2). Unsupervised graph anomaly detection: Catching new fraudulent behaviours. Grab Engineering.** https://engineering.grab.com/graph-anomaly-model [V] [SEA]. GraphBEAN autoencoder on GrabFood/GrabMart consumer-merchant bipartite graph; node and edge scores via reconstruction error; heuristic "fraud type tagger" (promo abuse, collusion); outputs feed human experts and automatic blocking of promo use or transactions. Excellent for the "risk score then action" pipeline.
- **Grab Engineering (2022, Nov 24). Graph for fraud detection.** https://engineering.grab.com/graph-for-fraud-detection [V, intro only read] [SEA]. Applies R-GCN for fraud.
- **Meesho engineering blog, TrustMesh: real-time fraud brain over graphs and sequences.** https://www.meesho.io/blog/trustmesh-how-we-built-a-real-time-fraud-brain-that-thinks-in-graphs-and-sequences [V existence only; companion to TRUST; not read].
- **iFood x Neo4j case study** https://neo4j.com/customer-stories/ifood/ [V existence]. Vendor marketing (promo-abuse ring detection in Brazil). Use only as illustrative, flag as vendor-sourced.
- Cashfree RTO Intelligence docs (https://www.cashfree.com/docs/payments/checkout/cod/rto) [V existence]: practitioner example of "restrict high-risk COD to prepaid", i.e., the deflection pattern. Vendor docs.

## Philippine context (news / government; not peer-reviewed) [PH]
- Inquirer (2021). *DTI urges online payment to avoid fake food delivery bookings.* https://newsinfo.inquirer.net/1419459/dti-urges-online-payment-to-avoid-fake-food-delivery-bookings [V by search result; page returned 403 on direct fetch, details taken from search summary; author/date not retrieved]. Describes COD bookings sent to other addresses leaving the rider to absorb the cost; DTI recommends online payment; a Senate bill and an NBI probe request are mentioned.
- Inquirer (2020). *Social media group to the rescue of duped food couriers.* https://newsinfo.inquirer.net/1254895/social-media-group-to-the-rescue-of-duped-food-couriers/amp [V by search result; same caveat]. "Order Heroes" Facebook group; fake customers on COD.
- ABS-CBN (2023). *Survey: Pinoys prefer COD when online shopping.* https://abs-cbn.com/life/05/04/23/survey-pinoys-prefer-cod-when-online-shopping [V by search result only; contents not read]. A 2017 ABS-CBN piece cited a single-operator estimate of about 80% COD preference; treat as weak.

## Synthesis points
1. Closest precedents (DeFraudNet, TRUST, Grab GraphBEAN, VPGNN) all combine tabular features with graph links over shared identifiers (device, address); none is open or Philippine.
2. The deflection pattern (route risky COD to prepayment/challenge) appears in industry docs (Cashfree, Meesho "intercept before placement", Grab "block promo use"), but no academic paper evaluates the customer-friction cost of deflection. See [[Research_Gaps]].
3. For the Philippine problem the evidence is journalistic: rider-bearing fake COD bookings. No peer-reviewed quantification found.
4. No Foodpanda, GrabFood-PH, Gojek, Swiggy or Zomato academic fraud paper was retrieved [searched only via generic queries]. Treat as "not found", not "does not exist".
