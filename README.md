# 📊 Customer Churn & Retention Analysis
### Data Science & Analytics – Task 2 | Future Interns Internship Program 2026

---

## 🔍 Project Overview

This project analyzes customer churn and retention patterns for a telecommunications company using the **Telco Customer Churn Dataset**. The goal is to identify why customers leave, which segments are most at risk, and what actions a business can take to improve retention.

This analysis simulates real-world work done by data analysts in product, growth, and retention teams at SaaS and subscription-based businesses.

---

## ❓ Business Questions Answered

- What is the overall churn rate?
- Which customer segments are most likely to churn?
- How does contract type impact retention?
- Do higher monthly charges increase churn risk?
- How does customer tenure relate to churn likelihood?
- What are the most effective retention drivers?

---

## 📁 Repository Structure

```
customer-churn-analysis/
│
├── data/
│   └── telco_churn_clean.csv        # Cleaned dataset used in Power BI
│
├── dashboard/
│   └── churn_dashboard.pbix         # Power BI dashboard file
│
├── screenshots/
│   ├── overview_page.png            # Dashboard Page 1 – Overview
│   └── deep_dive_page.png           # Dashboard Page 2 – Deep Dive
│
└── README.md
```

---

## 📦 Dataset

**Source:** [Telco Customer Churn Dataset – Kaggle](https://www.kaggle.com/datasets/blastchar/telco-customer-churn)

- **Rows:** 7,043 customers
- **Columns:** 21 features including demographics, services subscribed, contract type, billing, and churn status
- **Target Variable:** `Churn` (Yes / No)

---

## 🛠️ Tools Used

| Tool | Purpose |
|------|---------|
| **Power BI Desktop** | Dashboard creation, DAX measures, data modeling |
| **Power Query** | Data cleaning and transformation |
| **DAX** | Custom KPI calculations and calculated columns |

---

## 🧹 Data Cleaning Steps

Performed in **Power Query Editor:**

- Converted `TotalCharges` from text to decimal (contained blank strings)
- Replaced errors in `TotalCharges` with `0`
- Verified no duplicate `customerID` values
- Confirmed `Churn` column values are consistently `Yes` / `No`

**Calculated Columns added via DAX:**

- `Tenure Group` – Bucketed tenure into 4 bands: 0–12, 13–24, 25–48, 49–72 months
- `Number of Services` – Counted total services subscribed per customer

---

## 📐 DAX Measures

```dax
Total Customers = COUNTROWS('telco-customer-churn')

Churned Customers = CALCULATE(COUNTROWS('telco-customer-churn'), 'telco-customer-churn'[Churn] = "Yes")

Churn Rate = DIVIDE([Churned Customers], [Total Customers], 0)

Retention Rate = DIVIDE([Retained Customers], [Total Customers], 0)

Revenue Lost (Monthly) = CALCULATE(SUM('telco-customer-churn'[MonthlyCharges]), 'telco-customer-churn'[Churn] = "Yes")
```

---

## 📊 Dashboard Pages

### Page 1 — Overview
- KPI Cards: Total Customers, Churn Rate, Retention Rate, Revenue Lost
- Churn vs Retained split (Donut Chart)
- Churn by Contract Type (Bar Chart)
- Churn by Tenure Group (Line Chart)
- Churn by Internet Service (Column Chart)

### Page 2 — Deep Dive
- Churn by Payment Method
- Avg Monthly Charges: Churned vs Retained
- Churn Rate by Number of Services
- Churn by Senior Citizen status
- Interactive slicers: Contract Type, Internet Service, Payment Method, Senior Citizen, Tenure Group

---

## 💡 Key Insights

1. **Overall churn rate is ~26%** — roughly 1 in 4 customers leaves the platform
2. **Month-to-month contract customers churn at 43%** — the highest of any segment
3. **2-year contract customers churn at only ~3%** — loyalty programs significantly reduce churn
4. **Fiber optic internet users have the highest churn** despite paying the most monthly
5. **Electronic check payers churn more** than customers using automatic payment methods
6. **Customers with 5+ services are significantly less likely to churn** — bundling increases stickiness

---

## ✅ Business Recommendations

| Recommendation | Target Segment |
|---------------|---------------|
| Offer discounts to convert month-to-month → annual contracts | Month-to-month customers |
| Launch auto-pay incentive campaigns | Electronic check payers |
| Investigate and improve fiber optic service quality | Fiber optic users |
| Create loyalty bundles to encourage multi-service adoption | Low-service customers |
| Develop early churn intervention for customers in 0–12 month tenure | New customers |

---

## 🚀 Skills Demonstrated

- Customer retention & churn analysis
- Cohort analysis and customer segmentation
- Business KPI development with DAX
- Interactive dashboard design in Power BI
- Data-driven business storytelling and recommendations

---

## 👤 Author

**[Your Name]**
Data Science & Analytics Intern — Future Interns 2026
🔗 [LinkedIn Profile](https://www.linkedin.com/in/yourprofile)
🔗 [Future Interns](https://www.linkedin.com/company/future-interns/)

---

## 📌 Acknowledgements

- Dataset: IBM / Kaggle – Telco Customer Churn
- Internship Program: [Future Interns](https://futureinterns.com)
