# Hypothesis Test Notes
**Experiment:** Campaign A/B Test — New Onboarding Flow
**Analyst:** Auto-generated | **Date:** 2026-06-27

---

## 1. Metric Tested
**Paid Conversion Rate** — proportion of users in each group who converted to a paid plan within 30 days.

### Why this metric?
This is the North Star metric because it directly measures business revenue impact. A campaign that improves conversion rate translates directly to increased subscriptions and revenue.

---

## 2. Hypotheses

**H₀ (Null):** The paid conversion rate in Treatment is equal to or lower than in Control.
> H₀: p_treatment ≤ p_control

**H₁ (Alternate):** The paid conversion rate in Treatment is greater than in Control.
> H₁: p_treatment > p_control

---

## 3. Test Design

| Parameter | Value |
|---|---|
| Test type | Two-proportion Z-test |
| Tails | One-tailed (testing for improvement only) |
| Significance level (α) | 0.05 |
| Minimum detectable effect | ~2% absolute lift |

---

## 4. Test Inputs

| Input | Control | Treatment |
|---|---|---|
| Group size (n) | 690 | 710 |
| Conversions | 22 | 50 |
| Conversion rate | 0.0319 (3.19%) | 0.0704 (7.04%) |
| Pooled proportion | 0.0514 | |
| Standard error | 0.01181 | |

---

## 5. Test Output

| Statistic | Value |
|---|---|
| Z-statistic | 3.2640 |
| P-value (one-tailed) | 0.000549 |
| α threshold | 0.05 |
| Decision | **REJECT H₀** |

---

## 6. Interpretation

Since p-value (0.000549) < α (0.05), we reject the null hypothesis.

**The treatment group shows a statistically significant improvement in paid conversion rate:**
- Control: 3.19%
- Treatment: 7.04%
- Relative lift: +120.9%

This means the new campaign/onboarding flow is very unlikely to have produced this result by random chance. The evidence supports the treatment being genuinely more effective at converting users to paid plans.

---

## 7. Guardrail Findings

While conversion improved significantly, two guardrail metrics showed concerning increases:

| Guardrail | Control | Treatment | Change | Risk |
|---|---|---|---|---|
| Refund rate | 0.00% | 0.42% | +0.42pp | ⚠️ Medium |
| Support ticket rate | 14.72% | 24.76% | +10.04pp | 🔴 High |
| Avg rev per converted user | ₹1,630 | ₹770 | -52.8% | 🔴 High |

The large drop in average revenue per converted user suggests the treatment may be attracting lower-value customers. The spike in support tickets indicates the new flow may be creating user confusion. These must be addressed before full launch.

---

## 8. Decision Rule

- If p-value < 0.05 AND guardrail metrics are acceptable → **Launch**
- If p-value < 0.05 BUT guardrail metrics show risk → **Conditional / Partial launch**
- If p-value ≥ 0.05 → **Do not launch**

**Current status:** p-value < 0.05 but guardrail metrics show significant risk.
**Recommendation:** Conditional launch — investigate guardrail issues first.
