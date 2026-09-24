# Customer Churn Analysis & Power BI Dashboard

A complete customer churn analytics project built using **Python, SQLite, Pandas, Matplotlib, Seaborn, and Power BI**.

The project analyzes customer, subscription, and support data to understand churn patterns, customer segments, revenue exposure, customer satisfaction, complaints, escalation, and churn risk.

---

## 📌 Project Overview

Customer churn is an important business problem because losing customers can affect recurring revenue and customer lifetime value.

This project combines data from three SQLite database tables:

- `db_customer`
- `db_subscription`
- `db_support`

The data was cleaned, transformed, merged, analyzed, and visualized in Python. The final processed dataset was then used to build an interactive **Power BI dashboard** with three analytical sections.

---

## 🎯 Business Objectives

The main objectives of this project are to:

- Measure overall customer churn and retention
- Identify customer segments with different churn patterns
- Analyze churn across plan, contract, subscription, age, gender, tenure, and state
- Understand customer support and satisfaction patterns associated with churn
- Identify major cancellation reasons
- Quantify monthly revenue at risk from churned customers
- Compare customer lifetime value (CLTV) between retained and churned customers
- Analyze churn-risk groups and their observed churn rates
- Create an interactive Power BI dashboard for business reporting


## 🛠️ Tools & Technologies

- **Python**
- **Jupyter Notebook**
- **Pandas** – data manipulation and analysis
- **NumPy** – numerical operations
- **Matplotlib** – visualization
- **Seaborn** – statistical visualization
- **SQLite** – database querying
- **Power BI** – interactive dashboard and business reporting

## 📊 Data Sources

### 1. Customer Data

Main customer-level fields include:

- Customer ID
- Customer Name
- Country
- State
- Gender
- Date of Birth

### 2. Subscription Data

Main subscription and churn fields include:

- Subscription Start Date
- Subscription Type
- Renewal Date
- Plan Type
- Contract Type
- Cancellation Date
- Cancellation Reason
- Monthly Charges
- CLTV
- Churn Score

### 3. Support Data

Main support fields include:

- Customer ID
- Complaint Date
- Escalation Status
- CSAT Score
- Support Comments

---

## 🧹 Data Preparation

The Python notebook performs the following data preparation steps:

1. Connects to the SQLite database
2. Reads the three source tables into Pandas DataFrames
3. Inspects table structure, data types, missing values, and duplicates
4. Cleans customer data
5. Standardizes gender values
6. Converts date columns to datetime format
7. Cleans subscription-related fields
8. Creates a `churn_flag` based on cancellation date
9. Converts escalation status into a numeric indicator
10. Calculates customer-level complaint counts
11. Sorts support records by complaint date
12. Keeps the latest support record for each customer for the final customer-level merge
13. Merges customer, subscription, and support information
14. Creates additional analytical features such as:
   - Age
   - Age Group
   - Tenure
   - Tenure Group
   - Churn Risk
   - CSAT Group
15. Creates the final processed dataset for analysis and Power BI

---

## 🔎 Key Analytical Areas

The notebook covers analysis across:

### Customer Demographics
- Gender
- Age
- Age Groups
- State
- Plan Type
- Subscription Type
- Tenure

### Churn Analysis
- Overall churn
- Churn by plan
- Churn by contract
- Churn by subscription type
- Churn by gender
- Churn by age group
- Churn by tenure group
- Churn by state
- Churn by churn-risk group
- Yearly churn trend

### Revenue Analysis
- ARPU / average monthly charges
- Revenue at risk
- Revenue lost by plan type
- Revenue at risk by contract type
- Monthly charges by churn status
- CLTV by churn status

### Support Analysis
- Churn by escalation status
- Churn by CSAT group
- Churn by complaint count
- Escalation rate by plan type
- Complaint and satisfaction analysis

### Cancellation Analysis
- Churned customers by cancellation reason
- Cancellation reason distribution
- Revenue impact by cancellation reason

---

## 📈 Key Findings

### Overall Churn

- **Total Customers:** 10,000
- **Churned Customers:** 2,774
- **Churn Rate:** 27.74%
- **Retention Rate:** 72.26%
- **Revenue at Risk:** 39,894.72
- **Average Monthly Charges / ARPU:** 14.01
- **Average Complaints per User:** 2.50

### Plan Type

Observed churn rates in the analysis:

| Plan Type | Churn Rate |
|---|---:|
| Basic | 25.59% |
| Standard | 28.38% |
| Premium | 30.56% |

### Contract Type

| Contract Type | Churn Rate |
|---|---:|
| Monthly | 36.39% |
| Annual | 17.13% |

### Churn Risk

| Churn Risk | Churn Rate |
|---|---:|
| Low | 22.97% |
| Med | 40.06% |
| High | 52.14% |

### CSAT

| CSAT Group | Churn Rate |
|---|---:|
| 0–20 | 47.03% |
| 21–40 | 38.64% |
| 41–60 | 28.91% |
| 61–80 | 21.15% |
| 81–100 | 13.79% |

### Customer Lifetime Value

| Churn Status | Average CLTV |
|---|---:|
| Retained | 464.22 |
| Churned | 249.75 |

### Revenue at Risk by Contract Type

| Contract Type | Revenue at Risk |
|---|---:|
| Monthly | 28,743.04 |
| Annual | 11,151.68 |

### Revenue Lost by Plan Type

| Plan Type | Monthly Revenue at Risk |
|---|---:|
| Basic | 8,535.61 |
| Standard | 17,046.51 |
| Premium | 14,312.60 |

### Main Cancellation Reasons

The largest recorded cancellation-reason groups include:

- No longer interested
- Too expensive
- Poor content quality
- Poor customer support
- Switched to competitor
- Personal reasons
- Technical issues

---

## 📊 Power BI Dashboard

The final Power BI report is divided into three sections.

### 1. Executive Overview

The Executive Overview focuses on the overall business picture.

Key visuals include:

- Churn Rate by Plan Type
- Revenue Lost by Plan Type
- Churn Rate by Contract Type
- Churned Customers by Cancellation Reason
- Churned Customers by Gender
- Churn Rate by Churn Risk
- Yearly Churn Trend
- Churn Rate by State
- Average Monthly Charges by Churn Risk

---

### 2. Customer Demographics

This page focuses on customer segmentation and churn patterns across customer groups.

Key visuals include:

- Churn Rate by Plan Type
- Churn Rate by Gender
- Churn Rate by Age Group
- Churned Customers by Age Group
- Churn Rate by Tenure Group
- Churn Rate by Subscription Type
- Customer Count by Gender
- Customer Count by Subscription Type

---

### 3. Revenue & Support Analysis

This page focuses on financial impact, customer value, and support-related churn indicators.

Key visuals include:

- Churn Rate by Escalation Status
- Revenue Lost by Plan Type
- Monthly Charges by Cancellation Reason
- Churn Rate by CSAT Group
- Revenue at Risk by Contract Type
- Average CLTV by Churn Status
- Churn Rate by Complaint Count
- Monthly Charges by Churn Status
- Escalation Rate by Plan Type

---

## 💡 Business Takeaways

The analysis highlights several areas that are useful for further business investigation:

- The overall churn rate is **27.74%** across the analyzed customer base.
- Monthly-contract customers have a higher observed churn rate than annual-contract customers.
- Higher churn-risk groups show higher observed churn rates.
- Lower CSAT groups show higher observed churn rates in the analyzed data.
- Churned customers have lower average CLTV than retained customers.
- Churn represents **39,894.72** in monthly revenue at risk.
- Standard plan customers account for the largest monthly revenue-at-risk amount among the three plans.
- “No longer interested” and “Too expensive” are the two largest recorded cancellation-reason categories.

These are descriptive findings from the analyzed dataset and should not be interpreted as proof of causation without further statistical analysis.


## ⚠️ Data & Analysis Notes

- The final analysis dataset contains **10,000 customer-level records**.
- The support source contains multiple records for some customers. Complaint counts are calculated before keeping the latest support record for the final customer-level merge.
- `churn_flag` is derived from the presence of a cancellation date.
- `churn_risk` is derived from the churn score.
- Age and current tenure are time-dependent calculations based on the date when the notebook is executed.
- CSAT analysis excludes missing CSAT scores.
- Missing complaint counts are treated as zero for complaint-count analysis.
- Some state-level groups are very small and should therefore be interpreted carefully.


## 👤 Author

**Adrij Das**

Customer Churn Analysis | Python | SQL | Power BI | Data Analytics

---

## ⭐ Project Summary

**From raw database tables → data cleaning → feature engineering → exploratory analysis → business insights → interactive Power BI dashboard.**

This project demonstrates an end-to-end data analytics workflow focused on customer churn, customer behavior, support experience, and revenue impact.
