# Telecom Customer Churn Analysis - Power BI

## Project Details

**What is Churn?**
Churn refers to the rate at which customers stop doing business with a company or service, typically expressed as a percentage of the customer base.

**What is a Churn Rate?**
Churn Rate, sometimes known as attrition rate, is the rate at which customers stop doing business with a company over a given period. The higher your churn rate, the more customers stop buying from your business. The lower your churn rate, the more customers you retain.

> Churn Rate = (Churned Customers / Total Number of Customers) x 100%

**What is Customer Churn?**
Customer Churn refers to the natural business cycle of losing and acquiring customers. Every company, no matter the quality of its products or customer service, experiences churn. It can occur due to dissatisfaction, competitive offerings, or changes in customer preferences.

---

## About the Data
The dataset is a Microsoft Excel file containing one table with 7,043 rows and 23 columns of PhoneNow Telecoms customer information, including customer Demographics, Account Information, and Service Subscriptions.

---

## Skills
- Data Cleaning
- Data Inspection
- Data Transformation
- Data Standardization
- Data Visualization

---

## Data Preparation

The data transformation was done using Power Query and loaded into Microsoft Power BI Desktop.

**Data Cleaning steps in Power Query Editor:**

- Changed data types for customerID, gender, SeniorCitizen
- Standardized payment method names (e.g. "Mailed check" → "Mailed Check", "Bank transfer (automatic)" → "Bank Transfer")
- Renamed columns: customerID → CustomerID, gender → Gender, tenure → Tenure

**Additional conditional columns created:**
- CitizenshipStatus: "Young Citizen" if SeniorCitizen = 0, else "Senior Citizen"
- ChurnStatus: "Churned" if Churn = "Yes", else "Retained"

---

## Data Modeling
The cleaned and transformed dataset was modeled in Power BI Desktop for analysis.

---

## Data Analysis (DAX Measures)

- Total Customers = COUNT(ChurnDataset[CustomerID])
- Churned Customers = CALCULATE(COUNTA('ChurnDataset'[CustomerID]), 'ChurnDataset'[Churn] IN { "Yes" })
- Retained Customers = CALCULATE(COUNTA('ChurnDataset'[CustomerID]), 'ChurnDataset'[Churn] IN { "No" })
- Churn Rate % = Churned Customers / Total Customers
- Monthly Revenue Loss = CALCULATE(SUM(ChurnDataset[MonthlyCharges]), ChurnDataset[Churn] = "Yes")
- Revenue Loss % = DIVIDE(Monthly Revenue Loss, SUM('ChurnDataset'[MonthlyCharges]), 0)

---

## Dashboard Pages

**Customer Demographics**
Churn rates visualized by gender, age, partner status, and dependents.

**Account Details**
Churn rates by tenure, contract type, payment method, paperless billing, monthly charges, total charges, and support tickets.

**Customer Subscriptions**
Churn rates by subscribed services — phone, internet, online security, online backup, device protection, tech support, and streaming.

---

## Insights

- Customers on Two-Year contracts show higher retention; most Month-to-Month customers are recently joined.
- Overall churn rate is 27%, with $16.06M in yearly charges and $456.12K in monthly charges at risk.
- 782 tech tickets and 2,747 admin tickets were opened by churned customers.
- Most churned customers had not signed up for Online Security or Tech Support.
- 42% of churned customers were using Fiber Optic as their internet service.

---

## Recommendations

- Encourage customers to switch from Month-to-Month to One-Year or Two-Year contracts.
- Offer targeted discounts to at-risk Month-to-Month customers.
- Educate customers on the benefits of Online Security and Tech Support services.
- Target a 5% increase in long-term contract sign-ups and automatic payment adoption yearly.
