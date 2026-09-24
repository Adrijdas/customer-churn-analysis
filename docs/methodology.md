# Methodology

## 1. Project Approach

This project follows a structured customer churn analysis workflow:

**Data Import → Data Cleaning → Feature Engineering → Data Integration → KPI Analysis → Exploratory Analysis → Visualization → Export for Dashboarding**

The analysis was performed in Python using the customer, subscription, and support data stored in the SQLite database.

---

## 2. Data Sources

The project uses three logical data areas from the SQLite database:

- **Customer data** – customer demographics and geographic attributes.
- **Subscription data** – subscription dates, plan, contract, monthly charges, CLTV, churn score, and cancellation information.
- **Support data** – complaint dates, escalation information, and CSAT scores.

The final customer-level analysis dataset is exported as a CSV file for downstream analysis and Power BI dashboard development.

---

## 3. Data Import

Python libraries used in the notebook include:

- NumPy
- Pandas
- Matplotlib
- Seaborn
- SQLite3

The notebook connects to the SQLite database using `sqlite3`, identifies the available tables, and loads each table into a Pandas DataFrame for analysis.

---

## 4. Data Cleaning

### 4.1 Customer Data

The following cleaning steps were applied:

- Renamed `name` to `customer_name` for clarity.
- Removed `interests` and `pincode` because they were not required for the dashboard analysis.
- Converted `dob` to a datetime data type.
- Standardized gender values by changing `Men` to `Male` and `Women` to `Female`.
- Filled missing `country` values using the existing `state` → `country` relationship where possible.

### 4.2 Subscription Data

- Converted `subscription_start_date`, `renewal_date`, and `cancellation_date` to datetime values.
- Corrected the spelling `Refferal` to `Referral` in `subscription_type`.

### 4.3 Support Data

- Removed `col_1`, which was almost entirely null and not useful for analysis.
- Removed the `comment` field from the working analysis table.
- Converted `complaint_date` to datetime format.
- Created a customer-level `complaint_count` based on the number of support records for each customer.
- Sorted support records by `complaint_date` and retained the latest support record per customer for the final customer-level merge.
- Converted escalation information into a numeric flag: `Y = 1`, otherwise `0`.

---

## 5. Feature Engineering

Several analytical fields were created from existing data.

### Churn Flag

A customer is considered churned when `cancellation_date` is present.

- `churn_flag = 1` → Churned
- `churn_flag = 0` → Not churned / retained

### High Risk Flag

A high-risk flag was created from `churn_score`:

- `churn_score >= 70` → `is_high_risk = 1`
- Otherwise → `is_high_risk = 0`

### Churn Risk Category

Customers were grouped into three risk categories using `churn_score`:

- **Low:** `< 50`
- **Medium:** `50–69`
- **High:** `>= 70`

### Customer Tenure

Tenure was calculated in days using the subscription start date and:

- cancellation date for churned customers, or
- the current date for customers without a cancellation date.

### Customer Age

Age was calculated from `dob` using the current date.

---

## 6. Data Integration

The main analysis DataFrame was created by joining the subscription and customer data using `customerid`, followed by the cleaned/deduplicated support data.

The final integrated dataset contains customer-level attributes required for churn, revenue, demographic, and support analysis.

A separate customer-level support aggregation (`support_agg`) was also created containing:

- Total complaints
- Escalated complaints
- Average CSAT

The exported analysis dataset is saved as CSV for use outside the notebook.

---

## 7. Key KPI Calculations

The notebook calculates the following major KPIs:

### ARPU

Average Revenue per User is calculated as the mean of `monthly_charges`.

### Average Customer Tenure

Mean customer tenure in days.

### Revenue at Risk

Sum of `monthly_charges` for customers where `churn_flag = 1`.

### Escalation Rate

Mean of the numeric `is_escalated` flag multiplied by 100.

### Average Complaints per User

Total complaint count divided by the number of unique customers.

### Escalation vs Churn Correlation

Pearson correlation is calculated between `is_escalated` and `churn_flag` using non-null observations.

---

## 8. Exploratory Analysis

The notebook explores churn from several business perspectives:

- Churn rate by plan type
- Churn rate by state
- Churn rate by tenure group
- Churn rate by contract type
- Churned customers by age group
- Monthly charges by churn status
- Churn rate by churn risk
- Average CLTV by churn status
- Cancellation reason analysis
- Churned customers by gender
- Churn rate by complaint count
- Churn rate by CSAT score range
- Revenue lost by plan type
- Relationship between selected categorical/numeric variables using a correlation heatmap
- Monthly charges by plan, gender, and churn-risk category using a categorical/FacetGrid analysis

---

## 9. Grouping Logic Used for Visualization

### Tenure Groups

- 0–1 Year
- 1–2 Years
- 2–3 Years
- 3–4 Years
- 4+ Years

### Age Groups

- 0–18
- 19–25
- 26–35
- 36–45
- 46–55
- 56–65
- 66–100

### CSAT Score Groups

The notebook uses the following bins:

- 0–20
- 21–40
- 41–60
- 61–80
- 81–100

For CSAT-based churn analysis, records with missing `csat_score` are excluded from the grouped calculation.

---

## 10. Dashboard Preparation

The cleaned and integrated dataset was exported to CSV and used as the main analytical source for the Power BI dashboard.

The Power BI report is organized into three sections:

1. **Executive Overview** – overall churn, revenue loss, risk, state, cancellation reason, and trend insights.
2. **Customer Demographics** – churn patterns across plan, gender, age, tenure, and subscription type.
3. **Revenue & Support Analysis** – revenue exposure, CLTV, CSAT, complaints, and escalation-related churn insights.

---

## 11. Reproducibility Note

Age and tenure calculations use the date on which the notebook is executed (`pd.Timestamp.today()`). Therefore, these two calculated fields can change when the notebook is rerun at a later date.

For a fully reproducible historical analysis, a fixed analysis/reference date can be used instead of the current date.

---

## 12. Output

The main output of the Python workflow is the cleaned, integrated customer-level CSV dataset used for analysis and Power BI dashboard development.
