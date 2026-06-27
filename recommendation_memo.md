# Recommendation Memo — Campaign A/B Experiment
**To:** Product & Growth Leadership
**From:** Analytics Team
**Date:** 2026-06-27
**Re:** Go/No-Go Decision — New Campaign Onboarding Flow

---

## Executive Summary

The A/B experiment testing a new campaign onboarding flow showed a **statistically significant +120.5% relative improvement in paid conversion rate** (3.17% → 6.99%, p=0.0006). However, this gain comes with serious risks: the support ticket rate nearly doubled (+68.6%) and average revenue per converted user fell by 52.8%. A **selective launch** is recommended — deploy to Mobile and Tablet users while investigating the revenue quality and support load issues before full rollout.

---

## 1. Business Problem

The company needs to decide whether to fully launch a new campaign onboarding flow to all users. This decision impacts the Growth, Product, and Customer Success teams. The key metric to improve is paid conversion rate, while ensuring revenue quality, customer satisfaction, and operational costs are not harmed.

---

## 2. North Star Metric

**Paid Conversion Rate** was selected as the North Star metric because it directly measures the experiment's core objective — turning free/trial users into paying customers — and is the most direct indicator of revenue growth.

Supporting metrics (trial start rate, onboarding completion rate, engagement score) explain *why* conversion changed, while guardrail metrics (refund rate, support ticket rate, revenue per converted user) ensure conversion improvement is sustainable.

**Risk of blind optimisation:** If optimised without guardrails, a campaign could attract low-intent users who convert but then refund or generate high support costs, resulting in negative net revenue.

---

## 3. KPI Tree Summary

North Star: **Paid Conversion Rate**
- Funnel Progression → Landing Page Visit Rate → Trial Start Rate → Onboarding Completion Rate
- User Experience → Engagement Score → Days to Convert → Feature Adoption
- Acquisition Quality → Traffic Source Mix → Plan Type Distribution → Device Reach
- Guardrails: Refund Rate | Support Ticket Rate | Avg Revenue per Converted User

---

## 4. Experiment Results

| Metric | Control | Treatment | Lift | Signal |
|---|---|---|---|---|
| Users | 693 | 715 | — | |
| Landing Page Visit Rate | 63.64% | 72.59% | +14.1% | ✅ |
| Trial Start Rate | 25.11% | 29.09% | +15.8% | ✅ |
| Onboarding Completion Rate | 15.58% | 21.26% | +36.5% | ✅ |
| **Paid Conversion Rate** | **3.17%** | **6.99%** | **+120.5%** | ✅ |
| Avg Revenue per User | ₹51.75 | ₹53.88 | +4.1% | ✅ |
| Avg Revenue per Converted User | ₹1,630 | ₹770 | **-52.8%** | 🔴 |
| Refund Rate | 0.00% | 0.42% | +0.42pp | ⚠️ |
| Support Ticket Rate | 14.72% | 24.76% | +68.6% | 🔴 |
| Avg Engagement Score | 57.03 | 62.93 | +10.3% | ✅ |
| Avg Days to Convert | 8.86 | 6.40 | -27.7% | ✅ |

---

## 5. Hypothesis Test Result

- **Test:** Two-proportion Z-test (one-tailed), α = 0.05
- **Z-statistic:** 3.2640
- **P-value:** 0.000549
- **Decision:** Reject H₀ — conversion improvement is statistically significant
- **Interpretation:** The probability of observing this result by chance is less than 0.06%. The treatment effect on conversion is real.

---

## 6. Guardrail Analysis

| Guardrail | Finding | Risk Level |
|---|---|---|
| Refund Rate | Rose from 0.00% to 0.42% in Treatment | ⚠️ Medium — worth monitoring |
| Support Ticket Rate | Rose from 14.72% to 24.76% — a +68.6% increase | 🔴 High — signals user confusion |
| Avg Rev per Converted User | Dropped from ₹1,630 to ₹770 (-52.8%) | 🔴 High — lower-quality conversions |

The conversion lift is real, but the revenue quality concern is significant. Despite more users converting, each converted user generates far less revenue, suggesting the new flow may be attracting lower-intent users or encouraging lower-tier plan selection.

---

## 7. Segment-Level Insights

| Segment | Standout Finding |
|---|---|
| **Mobile users** | Treatment conversion 7.34% vs Control 2.57% — strongest uplift (+185%) |
| **Tablet users** | Treatment conversion 7.14% vs Control 1.79% — strongest relative lift |
| **Free plan users** | Treatment 9.24% vs Control 3.05% — highest absolute lift |
| **North region** | Treatment 8.89% vs Control 3.45% — best regional response |
| **West region** | Treatment 5.03% vs Control 3.38% — weakest lift; may need separate treatment |

---

## 8. Final Recommendation

### ✅ LAUNCH — for Mobile and Tablet users only

**Rationale:**
- Conversion improvement is statistically significant and practically meaningful (+120.5%)
- Mobile and Tablet segments show the strongest and most consistent uplift
- Engagement and funnel metrics all improved, indicating genuine user quality improvement

**Conditions before full launch:**
1. Investigate the support ticket spike — identify which step in the new flow is causing confusion and resolve it
2. Analyse the revenue per converted user drop — determine if lower-tier plans are being defaulted to and fix plan selection UX
3. Monitor refund rate for at least 2 more weeks; if it exceeds 1%, pause and investigate

---

## 9. Risks and Limitations

- **Revenue quality risk:** More conversions at lower value could net-negative vs fewer high-value conversions
- **Support cost risk:** A 68.6% increase in support tickets increases operational costs significantly
- **Segment imbalance:** West region showed minimal lift; a one-size-fits-all launch may underperform
- **Duration:** Experiment duration is not specified; if run for fewer than 2 weeks, results may not account for weekly seasonality
- **Outliers:** A small number of high-revenue Control users ($6K–$8K) inflate Control ARPU comparisons

---

## 10. Next Steps

1. Immediately launch to Mobile + Tablet users (these show strongest, cleanest lift)
2. Audit the new onboarding flow steps that most correlate with support ticket creation
3. Run a follow-up experiment fixing the plan selection step to improve revenue per user
4. Re-evaluate West region with a region-specific campaign variant
5. Set a 30-day post-launch monitoring dashboard tracking conversion rate, ARPU, and support load in real time
