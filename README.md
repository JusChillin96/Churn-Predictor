# 📉 Telecom Customer Churn Prediction

### A Business Intelligence project using XGBoost to predict customer attrition and calculate potential ROI.

![Python](https://img.shields.io/badge/Python-3.x-blue?style=flat&logo=python)
![Library](https://img.shields.io/badge/Library-XGBoost-orange?style=flat&logo=xgboost)
![Status](https://img.shields.io/badge/Status-Completed-green)

## 📌 Project Overview
Customer Churn (attrition) is the biggest threat to subscription businesses. In this project, I analyzed customer data from a Telco company to predict which users were likely to leave.

Unlike standard academic projects, I focused on **Profit Maximization**. I adjusted the model to prioritize **Recall** (catching the churners) over precision, calculating a hypothetical savings of **$106,900** on the test set.

## 📂 Dataset
The dataset is obtained from [Kaggle: Telco Customer Churn](https://www.kaggle.com/datasets/blastchar/telco-customer-churn).
*   **Rows:** 7,043 Customers
*   **Target:** `Churn` (Yes/No)
*   **Features:** Contract Type, Monthly Charges, Tenure, Internet Service, etc.

## 🛠️ Key Techniques
### 1. Handling Imbalanced Data
Only 26% of customers churned. A standard model was biased towards the majority class (Recall ~52%).
*   **Solution:** I implemented **Weighted XGBoost** (`scale_pos_weight`), telling the algorithm to penalize missing a churner 3x more than missing a non-churner.
*   **Result:** Recall improved to **~80%**, capturing the majority of at-risk customers.

### 2. Feature Importance Analysis
Using XGBoost's built-in importance metric, I identified the top drivers of churn:
1.  **Contract Type:** (Month-to-month customers are highest risk).
2.  **Fiber Optic Internet:** (Customers with this service churn frequently, suggesting technical issues).
3.  **Tenure:** (New customers are 3x more likely to leave than long-term ones).

### 3. Business ROI Calculation
I simulated a retention campaign:
*   **Cost of Losing Customer:** $500 (LTV)
*   **Cost of Incentive:** $50
*   **Net Savings:** By targeting the users identified by the model, the company saved **$106,900** in retained revenue compared to a "do nothing" approach.

## 🤖 Model Performance
**Algorithm:** XGBoost Classifier

Standard model

<img width="433" height="184" alt="image" src="https://github.com/user-attachments/assets/aec3b23d-0ad0-4cb2-afb1-ba9bb7fb151d" />

Weighted model

<img width="469" height="193" alt="image" src="https://github.com/user-attachments/assets/51730c40-c0cb-42dc-98f6-ac3d00e1ceeb" />

## 🚀 How to Run
1. Clone the repository:
   ```bash
   git clone https://github.com/JusChillin96/Churn-Predictor.git
