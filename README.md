# [Python] Linear Regression-House Loan Amount Prediction
This project implements a full-cycle linear regression workflow to predict housing loan amounts based on customer profiles and property characteristics. The dataset contains demographic, income, and property data for thousands of applicants.

## I. INTRODUCTION

### Problem Statement

A financial institution wants to predict how much loan a customer is eligible for, based on demographic and property data. The task is to help build a regression model that can accurately predict **Loan Sanction Amount (USD)**, and analyze key factors influencing loan decisions.

---

## II. EXPLORATORY DATA ANALYSIS
### Data Overview

- **Target Variable:** `Loan Sanction Amount (USD)`
- **Features:**
  - Gender, Age, Income (USD), Income Stability
  - Property Age, Property Location, Property Price

### Data Processing Step
1. **Exploratory Data Analysis (EDA)** using `pandas`, `matplotlib`, `seaborn`
2. Handling **missing values** & encoding categorical variables with `get_dummies`
3. Creating new features like:
   - **Loan-to-Value (LTV) Ratio**
   - **Loan-to-Income (LTI) Ratio**
   - **Borrower Risk Level** using quantile binning

---

## III. MODELING WORKFLOW

| Step | Description |
|------|-------------|
| Preprocessing | Cleaned and encoded data |
| Train-Test Split | 80/20 ratio |
| Model | Linear Regression (`scikit-learn`) |
| Evaluation | MAE, MSE, R² Score |

### Performance Metrics

- **MAE:** 127.84  
- **MSE:** 2,290,198.04  
- **R² Score:** 0.9978 ✅

### Feature Engineering
- **Loan-to-Value (LTV) Ratio**  
  Helps evaluate how much of the property’s value is covered by the loan.
  
- **Loan-to-Income (LTI) Ratio**  
  Used to assess financial risk. Customers were segmented into:
  - `Low Risk`
  - `Medium Risk`
  - `High Risk`
---
## IV. DATA PROCESSING & VISUALIZATION
![image](https://github.com/user-attachments/assets/c2731ce3-e5a1-4c62-b8b9-dd19aa2b4e87)

![image](https://github.com/user-attachments/assets/12e2e34a-0c85-4773-a98d-054bbe53fc42)

After reviewing the dataset, we started by removing missing values (81 rows) and confirming data types were consistent across numerical and categorical fields. 

![image](https://github.com/user-attachments/assets/1f6f9f62-16aa-4aae-9663-737dc0ac5c45)

To prepare the data:
- We used get_dummies() for categorical features (Gender, Property Location, Income Stability)
- Created two new engineered features:
  - Loan-to-Value Ratio (LTV) = Loan / Property Price
  - Loan-to-Income Ratio (LTI) = Loan / Income

- Based on LTI values, customers were segmented into:
  - Low Risk
  - Medium Risk
  - High Risk
![image](https://github.com/user-attachments/assets/49029a30-047d-476b-a500-3cf061167e7d)
![image](https://github.com/user-attachments/assets/475dde1c-d884-43bb-a090-f831b7699d85)
Divide the data into training and test sets with a suitable ratio (e.g., 80/20) to ensure unbiased model evaluation.

![image](https://github.com/user-attachments/assets/7f967d3a-c41e-43a1-9d47-9448d6f76072)
![image](https://github.com/user-attachments/assets/b07ab2b9-31a5-4364-a917-d1850f79e50e)
![image](https://github.com/user-attachments/assets/32391036-72b7-4fb6-a20e-812107155eac)
Train a Linear Regression model on the training set.

![image](https://github.com/user-attachments/assets/76d8488e-a3d7-4df0-9a22-41d18a35ebc1)
Evaluate the model performance on the test set.

---
## V. KEY INSIGHTS

### 1. Does income or income stability affect loan amounts?
![image](https://github.com/user-attachments/assets/89eb4d0a-f268-4975-926c-7dcbdc183f1a)
- **Income** has a stronger correlation with loan amount (r ≈ 0.39)
- **Income Stability** shows very weak correlation (r ≈ 0.07)
![image](https://github.com/user-attachments/assets/87b46065-5c1f-4358-99d5-e3ddf6558cd6)
![image](https://github.com/user-attachments/assets/010eedab-9bcf-4b57-bdc9-1833e8c95465)
- Regression confirms that income has a moderate positive effect on loan amounts. Higher income = higher loan amounts.
- Income strongly influences loan amounts, while income stability plays a minimal role.
- Banks prioritize income levels over stability when deciding loan approvals.

### 2. Property Location Impact
![image](https://github.com/user-attachments/assets/e097411e-076b-4c3d-93c0-f55fbfb0d1eb)
![image](https://github.com/user-attachments/assets/e9a180fa-0ed2-4e08-b259-8098eb4ea3f9)
- **No statistically significant** difference in loan amount between rural, urban, and semi-urban properties. (ANOVA p > 0.72)

### 3. Gender Bias?
![image](https://github.com/user-attachments/assets/496a83db-8183-49ac-8a2f-a84c0452885b)
![image](https://github.com/user-attachments/assets/e4b04cf3-d91c-42f4-8399-d258b4f92373)

- No evidence of gender bias found in loan sanction amounts. (p = 0.46)
### 4. Borrower Risk Segmentation (LTI-based)
![image](https://github.com/user-attachments/assets/e7e8d0bf-b885-4f00-8ff7-b29722ff7d04)

![image](https://github.com/user-attachments/assets/b4ee5a67-5d30-4cbe-81bd-582a8fc7ac76)

- Low-risk customers tend to receive higher average loans
- High-risk customers are more tightly distributed at lower values
- This segmentation can guide targeted financial strategies and risk management

---

## 📌 VII. ADDITIONAL INSIGHTS
| Segment             | Strategy & Action                                                                 |
|---------------------|-----------------------------------------------------------------------------------|
| **High Income**      | Offer premium loans, upsell with value-added services, and promote long-term plans. |
| **New Borrowers**    | Welcome offers, onboarding support, and small initial loans to build trust.       |
| **High Risk**        | Use stricter approval rules, offer smaller loans, or require co-signers.         |
| **Medium Risk**      | Encourage consistent payments, provide tiered benefits to reduce drop-off risk.  |
| **Urban Applicants** | Focus on digital engagement and mobile-first loan management tools.              |
| **Rural Applicants** | Ensure accessibility, education on product terms, and support in onboarding.     |
