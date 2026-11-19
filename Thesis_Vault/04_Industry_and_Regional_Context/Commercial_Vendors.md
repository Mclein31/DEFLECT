---
type: research-note
title: Commercial Fraud Vendors for Multi-Accounting and Promo Abuse
tags: [thesis, vendors, seon, sift, fingerprint, incognia, sardine, grabdefence, advance-ai]
last_updated: 2026-11-15
---

# Commercial Vendors

> Pricing comes from third-party review/blog pages unless marked official; treat as indicative. Capability descriptions come from vendor marketing - not independently verified. Retrieved 2026-11-15.

| Vendor | What it does (relevant part) | Pricing model / public numbers | Fit for PH food delivery | Sources |
|---|---|---|---|---|
| **SEON** | Fraud API; email/phone digital-footprint enrichment (checks which online services an email/phone is registered on - this is the commercial form of "OSINT enrichment"), IP proxy/VPN checks, device fingerprinting, custom rules | Official page: Starter listed **$699/mo**, Premium custom. Allowances (e.g., 2,500 checks) conflict across sources - UNVERIFIED. Hybrid platform + API-call billing. | Strong on multi-account/promo abuse; PH coverage of footprint data UNVERIFIED | [seon.io/pricing](https://seon.io/pricing/); [HyperVerge guide](https://hyperverge.co/blog/seon-pricing/) |
| **Fingerprint** | Browser/mobile device identification, Smart Signals (bot, VPN, etc.) | Usage-based; free tier ~1,000 calls/mo; Pro Plus from ~$99/mo (third party) vs "$200/$400 for 100k calls" (support article) - conflict; check current page | Device-ID building block, not a decision engine | [fingerprint.com/pricing](https://fingerprint.com/pricing/); [docs](https://docs.fingerprint.com/docs/pricing); [support](https://support.fingerprint.com/hc/en-us/articles/20691283117325-What-is-your-smallest-plan) |
| **Sift** | ML decisioning, account-abuse and promo-abuse, global network of signals | Contact sales; no chargeback guarantee (merchant keeps loss) | Possible, enterprise-oriented | [vendor comparison](https://vibereference.vercel.app/auth-and-payments/fraud-detection-providers) (secondary) |
| **Forter** | Real-time decisioning, chargeback guarantee | No public price; third-party estimate ~$81.8k/yr avg (Vendr data) - UNVERIFIED | Enterprise e-commerce; card-centric | [Kount-alternatives roundup](https://www.chargeback.io/blog/kount-alternatives) |
| **Riskified** | Chargeback guarantee, policy abuse | Third party: ~0.4% of approved transactions; no rate on vendor site | Card-not-present oriented; COD fit weak | [Vertice](https://www.vertice.one/vendors/riskified) |
| **Signifyd** | Guarantee model | Third party: e.g., $350/mo for $1,000 guarantee (1.25%) - UNVERIFIED | Card-not-present; weak for COD | [Redo comparison](https://redo.com/resources/articles/comparisons/fraud-platform-pricing) |
| **Ravelin** | Payments + marketplace fraud, graph/network linking | Custom; no public numbers | Marketplaces/food delivery (UK focus) | [Redo comparison](https://redo.com/resources/articles/comparisons/fraud-platform-pricing) |
| **Incognia** | Device + location behaviour for multi-accounting, promo abuse; targets food delivery, ride-hailing | No pricing found | Directly markets to delivery; has LATAM focus | [Incognia multi-account blog](https://www.incognia.com/blog/how-to-detect-multiple-accounts-in-food-delivery-apps); [BiometricUpdate](https://www.biometricupdate.com/202510/multi-account-creation-biggest-challenge-in-gig-economy-incognia-fraud-report-finds) |
| **Sardine** | Device intelligence, behavioural biometrics, promo abuse/multi-accounting, fraud rings | Not found | Fintech-first | [sardine.ai/identity-fraud](https://www.sardine.ai/identity-fraud) |
| **GrabDefence** (Grab) | Device intelligence, graph linking, from Grab's own fraud stack | Not public | SEA-native | [Grab story](https://www.grab.com/inside-grab/stories/grabdefence-anti-fraud-technology-for-southeast-asias-digital-age/) |
| **Trusting Social** | Telco-data fraud/credit scores, identity verification, mule-account detection (Vietnam, PH) | Not public; Vietnam stats are company claims | Banks/lenders; not delivery | [Fintech News PH](https://fintechnews.ph/67941/ai/trusting-social-uses-ai-telco-data-for-financial-inclusion-philippines/); [Daily Guardian](https://www.dailyguardian.com.ph/blog/trusting-social-marks-7-years-fights-fraud-with-ai) |
| **ADVANCE.AI** | PH presence since 2019; identity verification, anti-fraud, credit bureau (2024 partnership with CIC) | Not public | Banks/e-commerce | [ADVANCE.AI blog](https://blog.advance.ai/blog/going-digital-creating-a-secure-and-frictionless-digital-future-in-the-philippines); [BiometricUpdate, Aug 2024](https://www.biometricupdate.com/202408/advance-ai-solidifies-philippines-presence-with-credit-bureau-services) |

## Takeaways for the thesis
1. Guarantee-model vendors (Forter, Riskified, Signifyd) are built for card chargebacks; COD fraud has no chargeback, so they fit poorly. This supports a thesis positioning around **COD-specific, identity-linkage-based risk scoring**.
2. Device-intelligence vendors (Fingerprint, Incognia, Sardine, SEON) cover the device layer; the thesis should focus on the **identity-attribute linkage + deflection policy** layer on platform-held data.
3. SEON's email/phone footprint enrichment is the commercial analogue of OSINT enrichment and operates under vendor data-processing agreements - see Legal_and_Ethical_PH.md for why the thesis should not replicate it with scraping.
4. Snowflake/Databricks are covered by another agent; not researched here.
