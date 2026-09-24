# Data Dictionary — Processed Dataset

Source: `data/processed/exported_churn_data.csv`

| Column | Description | Type in processed CSV |
|---|---|---|
| `customerid` | Customer identifier | text |
| `subscription_start_date` | Subscription start date | date/text |
| `subscription_type` | Acquisition/subscription source type | category |
| `renewal_date` | Subscription renewal date | date/text |
| `plan_type` | Customer plan tier | category |
| `contract_type` | Contract duration/type | category |
| `cancellation_date` | Date the subscription was cancelled; blank for retained customers | date/text |
| `cancellation_reason` | Recorded reason for cancellation | category/text |
| `monthly_charges` | Monthly customer charge | numeric |
| `cltv` | Customer lifetime value | numeric |
| `churn_score` | Churn score used for risk classification | numeric |
| `churn_flag` | Derived churn indicator: 1 = churned, 0 = retained | integer |
| `customer_name` | Standardized customer name field | text |
| `country` | Customer country | category |
| `state` | Customer state/region | category |
| `gender` | Standardized gender | category |
| `dob` | Date of birth | date/text |
| `complaint_date` | Support complaint date | date/text |
| `escalations` | Escalation field from support data | numeric |
| `csat_score` | Customer satisfaction score | numeric |
| `is_escalated` | Derived numeric escalation indicator | numeric |
| `complaint_count` | Per-customer complaint count created during support-table preparation | numeric |
| `tenure_days` | Derived tenure duration in days | numeric |
| `age` | Derived customer age | integer |
| `churn_risk` | Derived risk band from churn score: low / med / high | category |
| `is_high_risk` | Derived binary flag for churn score >= 70 | integer |
