# Campaign A/B Experiment — Analysis Repository
**Date:** 2026-06-27

---

## Business Problem Statement

The product team has launched a new campaign onboarding flow and needs to determine whether to roll it out to all users. The decision affects the Growth, Product, and Customer Success teams. Success is measured primarily by **paid conversion rate**, while risks around revenue quality, refund rates, and support load must be monitored. Evidence required: statistically significant improvement in conversion rate (p < 0.05) with no material worsening of guardrail metrics.

---

## Repository Structure

```
├── README.md
├── analysis/
│   ├── experiment_analysis.xlsx     # Cleaned data + QA report
│   └── hypothesis_test_notes.md     # Full hypothesis test documentation
├── outputs/
│   ├── experiment_summary.xlsx      # Control vs Treatment metric comparison
│   ├── kpi_tree.png                 # KPI tree diagram
│   └── recommendation_memo.md       # Final recommendation
└── screenshots/
    ├── kpi_tree_preview.png
    └── hypothesis_test_output.png
```

---

## Task 4: Data Cleaning Notes

| Check | Finding | Action |
|---|---|---|
| Total rows | 1,408 | — |
| Duplicate user_ids | 8 duplicates | Removed; kept first occurrence |
| Missing device_type | 18 rows | Filled as 'Unknown' |
| Missing traffic_source | 24 rows | Filled as 'Unknown' |
| Missing engagement_score | 14 rows | Kept NaN; excluded from averages |
| Missing days_to_convert | 1,336 rows | Expected — non-converters have no value |
| Invalid binary values | None | No action needed |
| Revenue outliers | Max = ₹8,610 (14 outliers >₹1,500) | Retained; flagged in analysis |
| Group balance | Control=693, Treatment=715 | Slight imbalance; acceptable |
| Segment balance | All regions/devices represented in both groups | No imbalance detected |

---

## North Star Metric

**Paid Conversion Rate** — the proportion of users who converted to a paid plan.

This was chosen because it is the most direct measure of campaign success and revenue impact. All funnel metrics (landing page visit, trial start, onboarding completion) are drivers of this metric, while refund rate, support ticket rate, and revenue per converted user serve as guardrails.

---

## Key Results

- Paid conversion rate improved significantly: 3.17% → 6.99% (p=0.0006)
- Support ticket rate rose sharply: 14.72% → 24.76% (risk)
- Avg revenue per converted user dropped: ₹1,630 → ₹770 (risk)
- Strongest segments: Mobile, Tablet, Free plan, North region

**Recommendation: Selective launch to Mobile + Tablet users; fix guardrail issues before full rollout.**
