📊 Customer Churn Prediction System using Machine Learning
🔍 Project Overview

Customer churn is one of the biggest challenges for subscription-based businesses. Retaining existing customers is significantly cheaper than acquiring new ones, making early churn detection critical for business growth.

This project builds an end-to-end Machine Learning system to predict customer churn using behavioral, contract, pricing, and engagement signals. The focus is on early warning detection and recall optimization, ensuring that potential churners are identified before they leave.

🎯 Business Objective

Predict whether a customer is likely to churn

Minimize missed churners (False Negatives)

Provide actionable insights for retention teams

Balance recall and precision using threshold tuning

🧠 Key Idea

“Raw customer data does not predict churn — behavioral change does.”

Instead of relying only on static attributes, this project emphasizes feature engineering to capture:

engagement decay

pricing stress

contract risk

service usage depth

payment friction

🗂️ Project Structure
Customer-Churn-Prediction/
│
├── data/
│   ├── raw/
│   │   └── Telco-Customer-Churn.csv
│   └── processed/
│       └── churn_features.csv
│
├── notebooks/
│   ├── data_understanding.ipynb
│   ├── eda.ipynb
│   ├── feature_engineering.ipynb
│   └── modelling.ipynb
│
├── README.md
└── requirements.txt
📈 Exploratory Data Analysis (EDA)

EDA was question-driven, not plot-driven.

Key questions explored:

How does churn vary with tenure?

Are churners more common among short-tenure customers?

Do pricing and contract type influence churn?

Are low-engagement customers at higher risk?

Key Insights

~25% customers churn → moderate class imbalance

Churn is highest among short-tenure & month-to-month customers

Customers with low service usage and no auto-pay show higher churn

Fiber + high monthly charges increase churn risk

⚙️ Feature Engineering

Feature engineering was the most critical step of this project.

🔹 Behavioral Features

service_count

low_engagement

premium_user

household_stability

🔹 Contract & Pricing Signals

is_monthly_contract

long_term_contract

high_price

early_high_price

🔹 Payment & Friction Indicators

is_autopay

payment_friction

Target variable:

churn_flag = 1  → customer churned
churn_flag = 0  → customer retained

All raw categorical columns were removed after feature creation to reduce noise and improve model stability.

🤖 Modeling Approach

Two models were trained and compared:

1️⃣ Logistic Regression

Interpretable

Strong recall for churners

Suitable for production decision-making

2️⃣ Random Forest

Non-linear pattern capture

Slightly higher ROC-AUC

Used as a benchmark / challenger model

Class imbalance handled using:

class_weight="balanced"
📊 Model Performance Summary
Logistic Regression

Recall (Churn): 0.79

Precision (Churn): 0.50

F1-Score (Churn): 0.62

ROC-AUC: 0.8378

Random Forest

Recall (Churn): 0.78

Precision (Churn): 0.52

F1-Score (Churn): 0.62

ROC-AUC: 0.8413

🏆 Model Selection Rationale

Although Random Forest achieved slightly higher ROC-AUC, Logistic Regression was chosen as the primary model because:

Higher churn recall (fewer missed churners)

Better interpretability for business stakeholders

Easier threshold tuning for recall optimization

In churn prediction, missing a churner is costlier than offering retention to a loyal customer.

📌 Key Metrics Explained

Recall → How many churners were successfully identified

Precision → How many flagged churners actually churned

F1-Score → Balance between recall and precision

ROC-AUC → Overall ranking ability across thresholds

Recall was prioritized over accuracy due to class imbalance and business impact.

🚀 Future Improvements

Threshold tuning to further improve recall

Cost-sensitive evaluation

SHAP-based explainability

Deployment as a real-time churn scoring API

🧑‍💻 Tech Stack

Python

Pandas, NumPy

Scikit-learn

Matplotlib, Seaborn

Jupyter Notebook

✅ Final Takeaway

This project demonstrates how business understanding + feature engineering + metric awareness leads to effective churn prediction systems.
The solution is practical, interpretable, and aligned with real-world retention strategies.
