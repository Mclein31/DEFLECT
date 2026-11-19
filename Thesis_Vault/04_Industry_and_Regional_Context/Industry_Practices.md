---
type: research-note
title: How Industry Fights Multi-Accounting, Fake Orders and Promo Abuse
tags: [thesis, industry, graph, device-fingerprint, fraud, grab, delivery-hero, uber]
last_updated: 2026-11-15
---

# Industry Practices

> Source depth: derived from search summaries of each page (not full reads). Re-open before quoting. Engineering posts for DoorDash, Swiggy, Zomato, Meituan, Gojek, Shopee on this specific topic were **not found** in this pass - listed as gaps, not claims.

## Grab (most relevant: SEA, PH operator)
- **Graph service platform**: stores historical device-account data; returns adjacent account IDs or shared device IDs; motivating case is multiple accounts on shared physical devices. [Grab Eng: Graph service platform](https://engineering.grab.com/graph-service-platform)
- **Graph for fraud detection**: argues graph models need little feature engineering and fewer labels; uses a relational GCN (RGCN). [Grab Eng](https://engineering.grab.com/graph-for-fraud-detection)
- **Graph Networks / visualisation**: analysts view all users sharing a device or IP to expose device farms/syndicates; includes a false-positive example (a rental corporate account wrongly flagged, then unblocked). Useful for the thesis's false-positive discussion. [graph-networks](https://engineering.grab.com/graph-networks); [graph-visualisation](https://engineering.grab.com/graph-visualisation)
- **GrabDefence** (commercialised): device intelligence from attributes such as timezone/browser; account IDs, devices, IPs mapped into a graph. [Grab story](https://www.grab.com/inside-grab/stories/grabdefence-anti-fraud-technology-for-southeast-asias-digital-age/)
- PH operational measures: mass deactivation of fake-name accounts, flags for repeat cancellers, PHP 1,000 COD cap (see Problem_Evidence_PH).

## Delivery Hero (Foodpanda's parent)
- Graph-based fraud detection on Amazon Neptune: "voucher abuse is a graph problem"; reported +32% blocked fraudulent purchases. [AWS Database Blog](https://aws.amazon.com/blogs/database/empowering-fraud-detection-at-delivery-hero-with-amazon-neptune) (publication date UNVERIFIED)
- In-house global payment fraud system: [Delivery Hero Tech Blog](https://tech.deliveryhero.com/how-we-developed-our-own-global-internal-payment-fraud-system-at-delivery-hero) (details UNVERIFIED - not read).

## Uber / Uber Eats
- Relational graph learning for collusion: users linked by shared info; RGCN via DGL; label = chargeback within a window; distinguishing edge types improves signal. [Uber Eng](https://eng.uber.com/fraud-detection/)

## Meituan (academic collaboration)
- PromoGuardian: multi-relation fused GNN for group promo abuse; 93.15% precision on Meituan data. [arXiv 2510.12652](https://arxiv.org/html/2510.12652v1) (coordinate with literature agent)

## India (Zomato / Swiggy) - news-level only
- COD can be disabled for a customer's next orders after cancellations; merchant-side loss disputes. [BOOM](https://www.boomlive.in/boom-reports/zomato-food-delivery-cod-scam-ceo-deepinder-goyal-20831). No engineering posts found.

## Technique catalogue (what to include in the thesis taxonomy)
| Technique | Evidence of industry use | Applicability to thesis |
|---|---|---|
| Shared-device/IP graph linking | Grab, Uber, Delivery Hero | Core. Simulate device_id/IP edges in synthetic data. |
| Identity-attribute linking (name, phone, email, address fuzzy match) | Vendors (SEON, Incognia, Sardine) market it; academic ER | Core thesis contribution; needs entity resolution. |
| Risk scoring (rules + ML/GNN) | All | Core. |
| COD cap / prepayment for risky orders ("deflection") | Grab PHP 1,000 cap; Zomato COD blocking after cancels; DTI advice | Core "deflection" action. |
| Phone OTP / SIM-registered numbers | PH SIM Registration Act (RA 11934) raises cost of burner numbers (law effect on fraud is UNVERIFIED) | Supporting signal. |
| Device intelligence / location behaviour | GrabDefence, Incognia | Simulate; do not collect real device data. |
| Account bans / suspensions | Grab (351k) | Outcome of scoring; discuss false-positive harm. |
| Rider-protection reimbursement | Grab 2021 | Out of scope; mention. |

## Gaps (to avoid claiming)
DoorDash, Swiggy, Zomato, Gojek, Shopee, Meituan engineering posts on multi-account linking: not found. Foodpanda PH-specific controls: not found.
