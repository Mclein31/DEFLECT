---
type: literature-note
title: Graph-based Fraud Detection
tags: [rrl, graph, gnn, community-detection, connected-components]
last_updated: 2026-11-15
---

# Theme 4: Graph-based fraud detection

[V] = verified via web search 2026-11-15.

## Graph construction and community detection
- **Connected components on shared identifiers** is the simplest baseline (accounts as nodes; edges = same phone / email / device / normalized address). No dedicated paper was cited for it; it is standard graph theory. Use Christen (2012) [[Entity_Resolution]] for the "transitive closure" step of ER, and Xiao et al. (2015) [[Multi_Account_and_Sybil_Detection]] for the cluster-then-classify precedent.
- **Blondel, V. D., Guillaume, J.-L., Lambiotte, R., & Lefebvre, E. (2008). Fast unfolding of communities in large networks. *Journal of Statistical Mechanics: Theory and Experiment*, P10008.** https://doi.org/10.1088/1742-5468/2008/10/P10008 (arXiv:0803.0476) [V]. Louvain modularity heuristic. Use to split giant components (e.g., one shared Wi-Fi IP or a shared "Santos" surname) into tighter communities.

## GNN models
- **Hamilton, W. L., Ying, R., & Leskovec, J. (2017). Inductive representation learning on large graphs. *NIPS 2017*.** arXiv:1706.02216 [V]. GraphSAGE: inductive, so it handles new accounts unseen at training. Venue (NIPS 2017) confirmed in search summary.
- **Schlichtkrull, M., Kipf, T. N., Bloem, P., van den Berg, R., Titov, I., & Welling, M. (2018). Modeling relational data with graph convolutional networks. *ESWC 2018*, LNCS 10843, 593-607.** https://doi.org/10.1007/978-3-319-93417-4_38 [V]. R-GCN for multi-relation graphs; the model Grab names for fraud (see [[Delivery_and_COD_Fraud]]). Fits a heterogeneous graph with edge types phone/device/address.
- **Dou, Y., Liu, Z., Sun, L., Deng, Y., Peng, H., & Yu, P. S. (2020). Enhancing graph neural network-based fraud detectors against camouflaged fraudsters. *CIKM 2020*, 315-324.** https://doi.org/10.1145/3340531.3411903 [V]. CARE-GNN: feature and relation camouflage; Yelp and Amazon datasets. Relevant because abusers can deliberately vary names/addresses to evade matching.
- **Liu, Y., Ao, X., Qin, Z., Chi, J., Feng, J., Yang, H., & He, Q. (2021). Pick and choose: A GNN-based imbalanced learning approach for fraud detection. *WWW '21*, 3168-3177.** https://doi.org/10.1145/3442381.3449989 [V]. PC-GNN: label-balanced sampler plus neighbor sampler for class imbalance. AUC figures (Amazon 95.86, Yelp 79.87) come from Papers with Code, a secondary source.
- **Wen et al. (2023), VPGNN (CIKM)** and **Mathew et al. (2021), DeFraudNet**: see [[Delivery_and_COD_Fraud]] for delivery/voucher graph use.

## Reviews and benchmarks (guard against "just use GNNs")
- **Tang, J., Hua, F., Gao, Z., Zhao, P., & Li, J. (2023). GADBench: Revisiting and benchmarking supervised graph anomaly detection. *NeurIPS 2023 Datasets and Benchmarks*.** arXiv:2306.12251 https://proceedings.neurips.cc/paper_files/paper/2023/hash/5eaafd67434a4cfb1cf829722c65f184-Abstract.html [V; author list from memory, confirm]. 29 models, 10 datasets; tree ensembles with simple neighborhood aggregation can beat specialized GNNs, with better AUPRC and Recall@K in fully supervised settings. Key justification for a GBDT + graph-derived-features design instead of an end-to-end GNN.
- **Motie, S., & Raahemi, B. (2024). Financial fraud detection using graph neural networks: A systematic review. *Expert Systems with Applications, 240*, 122156.** https://doi.org/10.1016/j.eswa.2023.122156 [V]. 33 articles from 388 records; GNN use mostly supervised/semi-supervised, little unsupervised and edge-/graph-level work.
- **Cheng, D., et al. (2025). Graph neural networks for financial fraud detection: A review. *Frontiers of Computer Science*.** arXiv:2411.05815 [V; author list beyond first not retrieved]. 100+ studies.

## Synthesis points
1. Public GNN fraud benchmarks (Yelp, Amazon reviews) are not delivery/COD data; PromoGuardian's PPA dataset (Meituan) is the closest, if truly released.
2. Evidence (GADBench; VPGNN) says heavy GNNs are not reliably better than strong tabular baselines, which suits a 4th-year prototype built on graph-derived features (component size, degree, shared-identifier counts) + XGBoost/LightGBM.
3. Camouflage (CARE-GNN) motivates multi-signal matching rather than exact identifiers.
