---
type: literature-note
title: Multi-Account, Sybil and Fake Account Detection
tags: [rrl, sybil, fake-accounts, multi-account, social-graph]
last_updated: 2026-11-15
---

# Theme 2: Multi-account / Sybil / fake-account detection

[V] = verified via web search 2026-11-15.

| Source | What it does | Why it matters to us |
| :-- | :-- | :-- |
| Cao, Sirivianos, Yang, & Pregueiro (2012). Aiding the detection of fake accounts in large scale social online services. *NSDI '12*, 197-210. https://www.usenix.org/conference/nsdi12/technical-sessions/presentation/cao [V] | SybilRank: ranks users by likelihood of being fake using social-graph trust propagation; at Tuenti nearly 100% (50K) and 90% (200K) of top-ranked accounts were fake vs about 5% for user-report approach. | Shows ranking + human review is a deployable pattern. But it needs a social graph; a food platform has none, only shared-identifier graphs. |
| Boshmaf et al. (2015). Integro: Leveraging victim prediction for robust fake account detection in OSNs. *NDSS 2015*. https://doi.org/10.14722/ndss.2015.23260 [V] | Predicts "victims", reweights graph edges; up to an order of magnitude better precision than SybilRank at Tuenti. | Idea of down-weighting unreliable edges transfers: weak shared identifiers (shared Wi-Fi/IP, common surname) should get low edge weight. |
| Yang, Wilson, Wang, Gao, Zhao, & Dai (2011). Uncovering social network sybils in the wild. *IMC '11*. arXiv:1106.5321 [V] | Renren ground truth: Sybils do NOT form tight clusters; they blend into the graph; links between Sybils mostly accidental. Extended in ACM TKDD 2014. | Cautions that pure graph-community assumptions fail; behavioral/profile features are needed alongside graph structure. |
| Xiao, Freeman, & Hwa (2015). Detecting clusters of fake accounts in online social networks. *AISec 2015 (ACM CCS workshop)*, 91-101. dblp: https://dblp1.uni-trier.de/rec/conf/ccs/XiaoFH15.html [V] | LinkedIn: cluster newly registered accounts, then classify the whole cluster using distribution of field values (names, emails) across the cluster. | Closest published analogue to our core idea (group accounts sharing/similar identity fields, then judge the group). Strong anchor. Note: DOI not confirmed in this session. |
| Al-Qurishi et al. (2017). Sybil defense techniques in online social networks: A survey. *IEEE Access, 5*, 1200-1219. https://doaj.org/article/c737e87cf14147279b516ca3a1dd52cd [V] | Taxonomy of Sybil defenses, literature 2006-2016. | Survey for the RRL background paragraph. Author list beyond first author not retrieved. |
| Dehkordi, M. R., & Zehmakan, A. N. (2025). Graph-based fake account detection: A survey. arXiv:2507.06541. https://arxiv.org/abs/2507.06541 [V] | Recent survey: graph topology + account attributes. | Recent (2025) survey; preprint, not peer-reviewed as of search. First-name initials not confirmed. |

## Synthesis points
1. Platform-scale fake-account work is dominated by social networks (Tuenti, Renren, LinkedIn, Facebook) with social edges. Delivery platforms have transaction and identifier edges, not friendship edges, so SybilRank-style trust propagation is not directly applicable.
2. The LinkedIn cluster approach (Xiao et al.) is the best conceptual precedent: build clusters from shared fields, then classify clusters.
3. Multi-account on delivery platforms is only partly "fake": the same person legitimately holds a personal and a work account, or family members share a phone/address. Sybil literature assumes malicious intent; our thesis must separate "linked" from "abusive" (see [[Privacy_and_Ethics]]).

## Not found (document as search limitations)
- No academic-grade Uber / DoorDash / Foodpanda engineering paper on multi-account detection was retrieved; only Grab blog posts (see [[Delivery_and_COD_Fraud]]). Facebook's own fake-account papers beyond SybilRank were not searched [UNVERIFIED].
