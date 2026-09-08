# Olist E-Commerce Analytics Dashboard

A multi-page Power BI dashboard built on the Olist Brazilian e-commerce dataset, designed to answer key business questions around customer behavior, sales performance, delivery operations, and order problems.

# Overview

## The dashboard is organized into four pages:

- Customer Behavior — RM (Recency-Monetary) segmentation using a 3×3 NTILE grid, CLV scoring, and churn status, with a business-driven pivot away from traditional RFM after finding that ~97% of customers were one-time buyers
- Sales & Revenue — Revenue stream modeling, category commission analysis, payment method breakdown, and Pareto (80/20) analysis
- Delivery Performance — Delivery classification logic, YoY KPI comparisons, and dynamic visual indicators for on-time vs. late delivery trends
- Orders & Problems — Root-cause investigation into customer retention, testing hypotheses across review scores, delivery time, price, and product category

# Tech Stack
SQL Server — data modeling, views, and business logic (segmentation, CLV, delivery classification)
Power BI / DAX — KPI measures, time intelligence, dynamic visuals
Python (pandas) — initial data exploration

# Key Findings
## Customer Behavior:
- Traditional RFM was statistically meaningless for this dataset — ~97% of customers were one-time buyers, making the "Frequency" dimension useless. Pivoted to an RM (Recency-Monetary) segmentation using a 3×3 NTILE grid instead, which produced far more actionable customer segments.
- Built CLV scoring and churn status (based on recency) to complement the segmentation, giving a clearer picture of customer value beyond simple purchase counts.
## Sales & Revenue
- Tested a shipping margin model as a potential revenue KPI, but abandoned it after finding ~22% of rows violated the model's core assumptions — a reminder that a metric has to hold up across the full dataset, not just the majority case.
- Settled on category commission as the primary revenue KPI, since it was more consistent and interpretable across product categories.
- Ran payment method breakdowns and a Pareto (80/20) analysis, confirming that a small subset of categories/sellers drive the majority of revenue.
## Delivery Performance
- Built delivery classification logic (late_type, order_segment) to categorize orders by how and why they were late, rather than just flagging "late vs. on-time."
- Delivery-related KPIs (on-time rate, YoY trends) were tracked with dynamic visual indicators, making performance shifts easy to spot at a glance.
## Orders & Problems — the core business question
- Investigated why ~97% of customers never return, testing delivery time, review scores, price, and product category as potential drivers.
- None of these operational factors showed a strong enough correlation to fully explain the one-time-buyer pattern. The conclusion: retention is more likely driven by platform or behavioral factors (e.g., how Olist's marketplace model connects customers to sellers) rather than something fixable through delivery or pricing changes alone.
- This reframed the business question from "how do we reduce late deliveries" to "is repeat purchase even the right growth lever for this platform" — a more strategic, less purely operational insight.
