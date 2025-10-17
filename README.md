
#  Bank Customer Churn Analysis

##  About the Project

This project explores **why retail banking customers leave (churn)** and how to **predict churn** using machine learning.
Using a dataset of **10,021 customer records**, the notebook combines exploratory data analysis, churn pattern identification, and a baseline predictive model to uncover key churn drivers and provide actionable business insights.

###  Goal

To help the bank:

* Identify high-risk customers before they churn
* Understand key behavioral and demographic churn indicators
* Design targeted retention and re-engagement strategies

---

## Why This Project

Customer churn directly affects a bank’s profitability and growth. Understanding why customers leave enables the organization to improve retention, reduce marketing costs, and enhance loyalty.

This project applies **data-driven churn analysis** to:

* Reveal churn patterns across geography, age, and activity
* Build a predictive model to detect at-risk customers
* Translate technical findings into actionable retention strategies

---

## Methodology

### Dataset

* 10,021 customers from a retail bank
* Key features: `Geography`, `Gender`, `Age`, `Tenure`, `Balance`, `NumOfProducts`, `IsActiveMember`, `EstimatedSalary`, and `Exited (Churn)`

### Preprocessing

* Checked for missing values and summary statistics
* Encoded categorical features (`Geography`, `Gender`) using OneHotEncoder
* Scaled numerical features with `StandardScaler` for model consistency
* Addressed class imbalance using **SMOTE (Synthetic Minority Oversampling Technique)**

### Exploratory Data Analysis

* Visualized churn by geography, age, balance, and customer activity
* Found **Germany** had the highest churn rate, especially among high-balance customers
* Observed that **customers aged 41–60** and **inactive users** were more likely to leave

### Modeling

* Implemented **Logistic Regression** as a baseline model
* Evaluated using **Recall**, **Precision**, and **ROC-AUC** metrics
* Chose Logistic Regression for interpretability, simplicity, and baseline benchmarking before testing complex models

---

##  Evaluation Metrics

* **ROC-AUC (≈ 0.787):** Good ability to distinguish churners from non-churners
* **Recall (≈ 0.715):** Correctly identified most churners — prioritized since missing a churner is costlier
* **Precision (≈ 0.395):** Acceptable for early churn detection where recall is more critical
* **Accuracy:** Moderate — balanced recall/precision trade-off

---

##  Challenges

**Class Imbalance:**
Only ~20% of customers churned, leading to imbalance.
✅ Solved using **SMOTE** to synthetically oversample minority churn cases, improving recall.

**Feature Correlation:**
Features like **Balance**, **Age**, and **Activity** were interrelated, making interpretation challenging.
✅ Addressed by scaling features and relying on **regularized Logistic Regression** for stability.

**Geographical Skew:**
Germany had a higher churn share, which could bias predictions.
✅ Solved using **One-Hot Encoding** for `Geography` and performing region-wise churn analysis.

---

##  Results & Insights

| **Insight Area**          | **Observation**                                                           | **Business Implication**                                                                       |
| ------------------------- | ------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| **Overall Churn Rate**    | ~20.4% of customers exited                                                | Indicates moderate attrition; highlights opportunity for proactive retention.                  |
| **Geography**             | Germany showed the highest churn, especially among high-balance customers | Premium customers may be dissatisfied — need personalized service retention.                   |
| **Age**                   | Customers aged 41–60 churned the most                                     | Mid-career clients reassess financial providers; retention campaigns should target this group. |
| **Activity**              | Inactive users churned significantly more                                 | Engagement strongly predicts loyalty; low-activity customers require reactivation strategies.  |
| **Balance**               | Medium and high balances correlated with churn in specific regions        | High-value customers may seek better financial returns or service experiences.                 |
| **Products**              | Customers with more products still churned                                | Product variety alone doesn’t guarantee satisfaction — clear communication and value are key.  |
| **Tenure & Credit Score** | Weak correlation with churn                                               | Behavioral and engagement factors are stronger churn predictors than demographics.             |

---

##  Model Performance

| **Metric**     | **Value**                        | **Interpretation**                                                          |
| -------------- | -------------------------------- | --------------------------------------------------------------------------- |
| **Model Used** | Logistic Regression (with SMOTE) | Interpretable, stable baseline for binary classification.                   |
| **ROC-AUC**    | **0.787**                        | Good separation between churners and non-churners.                          |
| **Recall**     | **0.715**                        | High sensitivity — successfully identifies most churners.                   |
| **Precision**  | **0.395**                        | Acceptable — moderate false positives, suitable for early retention alerts. |
| **Accuracy**   | Moderate                         | Balanced trade-off between recall and precision, effective baseline model.  |

---

##  Recommendations

| **Focus Area**                          | **Recommended Action**                                                | **Expected Outcome**                                     |
| --------------------------------------- | --------------------------------------------------------------------- | -------------------------------------------------------- |
| **High-Balance Customers (Germany)**    | Introduce dedicated relationship managers and premium support.        | Improve satisfaction and loyalty of high-value clients.  |
| **Inactive Customers (France & Spain)** | Launch engagement campaigns, personalized rewards, and reminders.     | Increase retention by reactivating low-engagement users. |
| **Middle-Aged Customers (41–60)**       | Offer tailored digital experiences and cross-sell financial products. | Build stronger connections with mid-career customers.    |
| **Product Complexity**                  | Simplify product structure and clarify benefits.                      | Reduce churn due to confusion or overselling fatigue.    |
| **Churn Monitoring**                    | Integrate model predictions into CRM workflows.                       | Enable early detection and targeted retention action.    |
| **Competitive Retention**               | Track competitor offers and market trends.                            | Ensure competitive pricing and customer experience.      |

---

##  Conclusion & Next Steps

This project demonstrates how **machine learning can identify customer churn patterns** and provide actionable insights for retail banking.
The **Logistic Regression model with SMOTE** achieved a strong **ROC-AUC of 0.787** and **Recall of 0.715**, showing reliable capability to detect churners.

### Key Takeaways

* **Primary Churn Drivers:** Geography, Age, Balance, and Activity
* **Business Focus:** Retain high-value and inactive customers through personalized engagement and improved service quality

### Next Steps

* Experiment with **ensemble models** such as Random Forest, XGBoost, and LightGBM for improved accuracy
* Incorporate **transactional and behavioral features** for deeper insights
* Deploy the churn model as a **dashboard** for real-time retention monitoring

---

##  Repository Contents

* `Dataviz.ipynb` — Exploratory analysis, churn insights, and model building
* `README.md` — Project documentation (you’re reading it!)

---

##  License

Released under the **MIT License**.


