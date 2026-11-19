---
type: literature-note
title: Risk Scoring, Imbalanced Learning and Explainability
tags: [rrl, imbalanced-learning, xgboost, lightgbm, isolation-forest, shap, pr-auc]
last_updated: 2026-11-15
---

# Theme 5: Risk scoring and decisioning

[V] = verified via web search 2026-11-15.

## Imbalanced classification
- **Chawla, N. V., Bowyer, K. W., Hall, L. O., & Kegelmeyer, W. P. (2002). SMOTE: Synthetic minority over-sampling technique. *Journal of Artificial Intelligence Research, 16*, 321-357.** https://doi.org/10.1613/jair.953 [V]. Caution for our case: synthetic oversampling of identity/graph features can create unrealistic accounts; prefer class weights/cost-sensitive loss and report both.
- **Dal Pozzolo, A., Boracchi, G., Caelen, O., Alippi, C., & Bontempi, G. (2018). Credit card fraud detection: A realistic modeling and a novel learning strategy. *IEEE Transactions on Neural Networks and Learning Systems, 29*(8), 3784-3797.** [V] (DOI not retrieved; locate via IEEE Xplore). Concept drift, class imbalance, delayed labels, and investigator feedback; argues for evaluating on top-k alerts that investigators can actually review. Directly supports human-in-the-loop + precision@k.
- Cost-sensitive learning foundation (Elkan, 2001) and practitioner COD-RTO class-weight advice: [UNVERIFIED for Elkan; the HackerNoon post https://hackernoon.com/using-data-science-to-deal-with-rtos was seen in search only and is a blog, not citable academically].

## Gradient boosting
- **Chen, T., & Guestrin, C. (2016). XGBoost: A scalable tree boosting system. *KDD '16*, 785-794.** https://doi.org/10.1145/2939672.2939785 [V].
- **Ke, G., et al. (2017). LightGBM: A highly efficient gradient boosting decision tree. *Advances in Neural Information Processing Systems 30*, 3146-3154.** https://proceedings.neurips.cc/paper/2017/file/6449f44a102fde848669bdd9eb6b76fa-Paper.pdf [V]. GOSS and EFB; up to 20x faster training than conventional GBDT.
- Industry evidence that boosting is a strong baseline: Meesho TRUST uses XGBoost as the baseline that its GNN+Transformer beats by about 9.6 points precision (see [[Delivery_and_COD_Fraud]]); GADBench finds tree ensembles competitive with specialized GNNs ([[Graph_Fraud_Detection]]).

## Anomaly detection
- **Liu, F. T., Ting, K. M., & Zhou, Z.-H. (2008). Isolation forest. *ICDM 2008*, 413-422.** https://doi.org/10.1109/ICDM.2008.17 [V]. Unsupervised, linear time. Useful when labels are absent (new fraud patterns). Grab's GraphBEAN is a graph-autoencoder analogue ([[Delivery_and_COD_Fraud]]).

## Evaluation metrics
- **Saito, T., & Rehmsmeier, M. (2015). The precision-recall plot is more informative than the ROC plot when evaluating binary classifiers on imbalanced datasets. *PLoS ONE, 10*(3), e0118432.** https://doi.org/10.1371/journal.pone.0118432 [V]. Justifies PR-AUC over ROC-AUC.
- Precision@k / Recall@K and AUPRC reported in GADBench (Tang et al., 2023) [V].
- False-positive cost: no single verified paper retrieved that quantifies customer-friction cost of false declines in food delivery; see [[Research_Gaps]]. Recommend defining a simple cost model (cost of rider loss + food waste vs lost order + churn) as thesis contribution.

## Explainability and human review
- **Lundberg, S., & Lee, S.-I. (2017). A unified approach to interpreting model predictions.** arXiv:1705.07874 [V]; (NIPS 2017 venue not confirmed in search; known from memory, confirm before citing). SHAP values for per-account reason codes.
- Human-in-the-loop: Grab's pipeline sends scores + tags to a human expert team ([[Delivery_and_COD_Fraud]]); Dal Pozzolo et al. (2018) formalize investigator feedback. No academic paper specific to delivery ops review queues was found.

## Synthesis points
1. A defensible design: ER-derived graph features + tabular + text features -> LightGBM/XGBoost -> calibrated risk score -> thresholded action (allow / challenge / require prepayment / review) with SHAP reason codes.
2. Report PR-AUC, precision@k, recall at fixed precision, and an explicit false-positive cost.
3. SHAP applies to tree models; explaining GNN decisions is harder, another argument for tabular-plus-graph-features.
