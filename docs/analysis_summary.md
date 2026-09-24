# Analysis Summary

## Project Overview

This project analyzes customer churn using customer, subscription, and support data. The analysis was performed in Python using the processed churn dataset generated from the SQLite database tables.

The main objective is to understand:

- Overall customer churn and retention
- Churn patterns across customer segments
- Revenue exposure associated with churn
- Customer support and satisfaction factors related to churn
- Churn-risk segments and their behavior

## Dataset Summary

- **Rows:** 10,000 customers
- **Columns in processed dataset:** 26
- **Main analysis fields:** customer ID, gender, date of birth, state, plan type, subscription type, contract type, monthly charges, CLTV, churn score, churn flag, churn risk, complaints, escalation status, and CSAT score.

## Key Business Metrics

| Metric | Result |
|---|---:|
| Total Customers | 10,000 |
| Churned Customers | 2,774 |
| Churn Rate | 27.74% |
| Retention Rate | 72.26% |
| ARPU / Average Monthly Charges | 14.01 |
| Revenue at Risk | 39,894.72 |
| Average Complaints per User | 2.50 |
| Average CLTV - Retained | 464.22 |
| Average CLTV - Churned | 249.75 |

## Customer Segment Analysis

### Churn Rate by Plan Type

| Plan Type | Churn Rate |
|---|---:|
| Basic | 25.59% |
| Standard | 28.38% |
| Premium | 30.56% |

### Churn Rate by Contract Type

| Contract Type | Churn Rate |
|---|---:|
| Annual | 17.13% |
| Monthly | 36.39% |

### Churn Rate by Subscription Type

| Subscription Type | Churn Rate |
|---|---:|
| Organic | 26.50% |
| Paid | 28.02% |
| Referral | 28.75% |

### Churned Customers by Gender

| Gender | Churned Customers |
|---|---:|
| Female | 1,401 |
| Male | 1,373 |

## Tenure and Risk Analysis

### Churn Rate by Churn Risk

The notebook creates churn-risk groups from the existing `churn_score`:

- **Low:** churn score < 50
- **Med:** churn score 50–69
- **High:** churn score >= 70

| Churn Risk | Customers | Churned Customers | Churn Rate |
|---|---:|---:|---:|
| Low | 7,836 | 1,800 | 22.97% |
| Med | 1,278 | 512 | 40.06% |
| High | 886 | 462 | 52.14% |

### CSAT and Churn

The notebook groups CSAT scores into five ranges and calculates mean churn rate after removing missing CSAT values.

| CSAT Group | Customers | Churned Customers | Churn Rate |
|---|---:|---:|---:|
| 0–20 | 757 | 356 | 47.03% |
| 21–40 | 1,848 | 714 | 38.64% |
| 41–60 | 2,791 | 807 | 28.91% |
| 61–80 | 2,203 | 466 | 21.15% |
| 81–100 | 1,233 | 170 | 13.79% |

### Churn Rate by Complaint Count

The notebook analyzes churn rate across the number of customer complaints. Missing complaint counts are filled with 0 before the analysis.

### Escalation and Churn

The processed data contains an `is_escalated` indicator where escalated cases are represented numerically for analysis.

- **Overall escalation rate:** approximately 23.35% when all 10,000 rows are used as the denominator.
- **Escalation rate by plan type** using the average of available `is_escalated` values:
  - Basic: 25.54%
  - Standard: 26.07%
  - Premium: 26.40%

The notebook also calculates the correlation between escalation and churn using rows with non-missing values.

## Revenue Analysis

### Revenue at Risk

Revenue at risk is calculated as the sum of `monthly_charges` for churned customers.

**Revenue at Risk = 39,894.72**

### Revenue Lost by Plan Type

| Plan Type | Monthly Revenue Lost |
|---|---:|
| Basic | 8,535.61 |
| Standard | 17,046.51 |
| Premium | 14,312.60 |

### Revenue at Risk by Contract Type

| Contract Type | Revenue at Risk |
|---|---:|
| Annual | 11,151.68 |
| Monthly | 28,743.04 |

## Cancellation Analysis

Among churned customers, the main cancellation reasons in the processed data are:

| Cancellation Reason | Churned Customers |
|---|---:|
| No longer interested | 712 |
| Too expensive | 556 |
| Poor content quality | 411 |
| Poor customer support | 399 |
| Switched to competitor | 258 |
| Personal reasons | 219 |
| Technical issues | 216 |

The notebook also calculates the percentage distribution of cancellation reasons among churned customers.

## Yearly Churn Trend

The notebook creates a yearly churn trend using the year extracted from `cancellation_date`.

| Cancellation Year | Churned Customers |
|---|---:|
| 2021 | 3 |
| 2022 | 77 |
| 2023 | 237 |
| 2024 | 470 |
| 2025 | 843 |
| 2026 | 1,144 |

## Customer Value

Average CLTV is calculated separately for retained and churned customers:

- **Retained customers:** 464.22
- **Churned customers:** 249.75

## Power BI Dashboard Summary

The final Power BI report is organized into three sections.

### 1. Executive Overview

The overview page focuses on high-level business performance and churn exposure, including:

- Churn Rate by Plan Type
- Revenue Lost by Plan Type
- Churn Rate by Contract Type
- Churned Customers by Cancellation Reason
- Churned Customers by Gender
- Churn Rate by Churn Risk
- Yearly Churn Trend
- Churn Rate by State

### 2. Customer Demographics

This page focuses on customer segmentation and behavioral differences across:

- Plan Type
- Gender
- Age Group
- Tenure Group
- Subscription Type
- Churn-related customer counts

### 3. Revenue & Support Analysis

This page focuses on financial impact and customer-support indicators, including:

- Churn Rate by Escalation Status
- Revenue Lost by Plan Type
- Monthly Charges by Cancellation Reason
- Churn Rate by CSAT Group
- Revenue at Risk by Contract Type
- Average CLTV by Churn Status
- Churn Rate by Complaint Count
- Monthly Charges by Churn Status
- Escalation Rate by Plan Type

## Analytical Takeaways

The analysis shows several patterns in the processed dataset:

1. Overall churn is **27.74%**, with **2,774 churned customers out of 10,000**.
2. Churn rate differs across plan and contract types.
3. Monthly-contract customers have a higher observed churn rate than annual-contract customers in the analyzed data.
4. Higher churn-risk groups show higher observed churn rates.
5. Lower CSAT groups show higher observed churn rates than higher CSAT groups.
6. Churn creates measurable monthly revenue exposure, with **39,894.72** in revenue at risk.
7. The largest recorded cancellation-reason groups are **No longer interested**, **Too expensive**, **Poor content quality**, and **Poor customer support**.
8. Churned customers have a lower average CLTV than retained customers in the processed data.
