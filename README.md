# 💰 Expense Anomaly & Budget Variance Detection System

### Advanced Excel · SQL · Power BI

This project presents an interactive **Budget Variance & Anomaly Detection Dashboard** developed using **Power BI** to help finance teams monitor departmental spending against budget in real time and catch unusual expense spikes before quarter-end reporting.

---

# 📸 Dashboard Preview

![Expense Anomaly & Budget Variance Dashboard](dashboard-preview(2).png)

*Interactive Power BI dashboard showing budget vs actual variance, department-wise overspend, category/region trends, and flagged anomalies.*

---

# 🎯 Business Problem

Companies allocate budgets to departments across expense categories (travel, salaries, training, utilities, marketing, infrastructure), but typically only discover overspending or unusual transactions when quarter-end financial reports are compiled — by which point the financial impact has already occurred.

This dashboard gives finance teams an early-warning system to identify overspending departments/categories and flag anomalous transactions on an ongoing basis, rather than after the fact.

---

# 📂 Dataset Overview

The raw dataset contains **10,010 individual transaction records** across **6 departments**, **6 expense categories**, and **5 regions**, spanning **3 years (2021–2023)**.

### Data Cleaning Performed

- Removed 12 duplicate Transaction IDs
- Dropped 1 record with a missing Transaction ID (unreliable row)
- Filled remaining null Department/Category/Region values as "Unspecified" (documented decision, not silently dropped)
- Result: **9,997 clean transaction records**

### Aggregation & Anomaly Detection

- Aggregated cleaned transactions to **1,298 monthly Department × Category records**
- Calculated variance % per record: `(Actual - Budget) / Budget * 100`
- Applied a **self-defined anomaly threshold of ±25% variance** to flag unusual spend — not a pre-labeled dataset, the anomaly logic was built from scratch
- **502 records flagged as anomalies**

### Attributes

- Date / Month, Department, Category, Region, Budget Amount, Actual Amount, Payment Method, Transaction ID, Variance %, Anomaly Flag

---

# ⚙️ Tools & Technologies

| Tool | Purpose |
|---|---|
| Advanced Excel | Initial data exploration, duplicate/null review, pivot tables |
| SQL | Data cleaning validation, monthly aggregation, anomaly-flagging logic, trend queries |
| Power BI | Interactive variance & anomaly monitoring dashboard |
| DAX | Budget/variance KPI measures |

---

# 📊 Dashboard Features

## 1. 📈 KPI Overview

KPI cards: Total Budget, Total Actual, Total Variance, Variance %, Anomaly Count.

---

## 2. 🏢 Department-wise Variance Analysis

Bar chart ranking departments by total overspend.

---

## 3. 🏷️ Category & Region Analysis

Category-wise average variance % (conditional formatting) and region-wise spend comparison.

---

## 4. 🚩 Anomaly Watchlist

Table of all flagged transactions sorted by variance %, with Month, Department, Category, Budget, Actual.

---

## 5. 📅 Monthly Trend

Line chart of total variance across the 3-year window.

---

# 💡 Key Insights

- Total actual spend exceeded budget by **₹8.4 crore (84M)** (₹82.0 crore (820M) actual vs ₹73.6 crore (736M) budgeted).
- **502 of 1,298** monthly department-category records (42%) were flagged as anomalies under the ±25% variance threshold.
- **Marketing** was the highest-overspend department (₹1.99 crore over budget), followed by HR (₹1.81 crore) and Sales (₹1.66 crore).
- Overspend patterns are consistent across the 3-year window rather than one-off events, indicating a structural budgeting gap.

---

# ✅ Recommendations

## 🚩 Real-Time Anomaly Alerts

Apply the 25% variance threshold as a live alert rule so finance teams are notified before month-end close, not after.

---

## 🏢 Department Budget Reallocation

Use department-wise variance trends (Marketing, HR, Sales) to renegotiate budgets in the next planning cycle.

---

## 🏷️ Category-Level Policy Review

Introduce pre-approval workflows for categories with consistently high average variance %.

---

## 📊 Continued Monitoring

Track variance monthly to validate whether corrective actions reduce overspend over time.

---

# 🚀 Usage Instructions

1. Open the Power BI dashboard file `expense_variance_dashboard.pbix`
2. Load `budget_actual_monthly_agg.csv` (and `budget_actual_cleaned.csv` for region/payment-method views) if required
3. Navigate through dashboard pages
4. Apply filters using: Department, Category, Region, Month
5. Analyze budget variance and anomaly trends

---

# 📁 Repository Structure

```text
Expense-Anomaly-Budget-Variance-Detection/
├── expense_variance_dashboard.pbix
├── budget_actual_cleaned.csv          # Cleaned transaction-level data
├── budget_actual_monthly_agg.csv      # Aggregated monthly data with variance & anomaly flags
├── sql_queries.sql                    # Schema, aggregation, and analysis queries
├── dax_measures.txt                   # DAX measures used in the report
├── dashboard-preview.png
└── README.md
