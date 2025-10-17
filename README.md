
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
* **Recall (≈ 0.715):** Correctly identified most churners prioritized since missing a churner is costlier
* **Precision (≈ 0.395):** Acceptable for early churn detection where recall is more critical
* **Accuracy:** Moderate balanced recall/precision trade-off

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

## Results & Insights

| **Insight Area** | **Observation** | **Business Implication** |
|------------------|-----------------|---------------------------|
| **Overall Churn Rate** | ~20.4% of customers exited | Indicates moderate attrition opportunity for proactive retention. |
| **Geography** | Germany shows the highest churn; France & Spain are lower overall | Prioritize retention efforts in **Germany**, especially among premium clients. |
| **Balance × Country** | **Germany:** churn highest among **very high balances**; **France/Spain:** churn highest among **medium balances** | Tailor retention by **balance tier per region** premium (Germany) vs. mid-tier (France/Spain). |
| **Activity (Contextual)** | In **Germany (very high balance)**, **inactive** customers churn more; in **France/Spain (medium balance)**, both active and inactive show elevated churn | Engagement matters but depends on financial profile design **segment-specific engagement strategies**. |
| **Satisfaction** | In FR/ES, inactive churners show **lower satisfaction**; in DE-VHB, satisfaction similar across groups | Improve **service experience** for inactive mid-balance users; for DE premium, address **pricing or product relevance**. |
| **Age** | Customers aged **41–60** churned the most | Mid-career clients often reassess financial providers target this segment with **personalized loyalty programs**. |
| **Products (Engagement)** | Customers with **3–4 products** still churned; satisfaction didn’t increase with more products | Product expansion ≠ loyalty focus on **value perception**, not quantity of products. |
| **Credit Score** | Only a mild difference lower scores churn slightly more, but trend is sequential | Creditworthiness has **limited impact** churn is driven more by satisfaction and engagement. |
| **Tenure & Credit Card** | Weak or no correlation with churn | Structural factors are **less predictive** focus on behavioral and emotional loyalty drivers. |

---

## Model Performance

| **Metric** | **Value** | **Interpretation** |
|-------------|------------|--------------------|
| **Model Used** | Logistic Regression (with SMOTE) | Chosen for its interpretability and reliability as a baseline classifier for binary churn prediction. |
| **ROC-AUC** | **0.787** | Indicates strong model discrimination, effectively distinguishes churners from non-churners. |
| **Recall** | **0.715** | High sensitivity  captures most true churners, prioritizing retention over false positives. |
| **Precision** | **0.395** | Moderate precision  acceptable when proactive churn prevention is the goal. |
| **Accuracy** | **≈ 71.8%** | Balanced performance across both classes; suitable for baseline deployment. |

### Key Insights

- The model achieved a **ROC-AUC score of 0.787**, showing strong ability to distinguish between churners and non-churners.  
- A **high recall of 0.715** indicates effective identification of churners critical for proactive customer retention.  
- **Moderate precision (0.395)** suggests some false positives, but this trade-off is acceptable since preventing churn outweighs the cost of extra outreach.  
- The **confusion matrix** confirms the model’s balance: it accurately predicts most non-churners while successfully capturing a large share of actual churners.  
- Overall, the **Logistic Regression with SMOTE** baseline offers interpretable, stable, and actionable predictions for early churn detection.



### Visual Interpretation:
- The **Confusion Matrix** reveals that while some false positives exist, the model achieves strong true positive detection.  
- The **ROC Curve** demonstrates good separation between churners and non-churners, validating the model’s predictive strength.


---

## Recommendations

| **Focus Area** | **Recommended Action** | **Expected Outcome** |
|----------------|------------------------|----------------------|
| **High-Balance Customers (Germany)** | Introduce **dedicated relationship managers**, loyalty benefits, and premium support tiers. | Strengthen satisfaction and loyalty among high-value customers, reducing attrition in a critical segment. |
| **Medium-Balance Customers (France & Spain)** | Launch **localized engagement campaigns** and targeted offers tailored to regional behavior. | Increase retention by addressing mid-tier customer needs with personalized communication. |
| **Inactive Customers** | Implement **reactivation workflows** such as personalized rewards, app engagement nudges, and periodic account insights. | Boost engagement and reduce churn by bringing back dormant users. |
| **Middle-Aged Customers (41–60)** | Offer **financial planning sessions** and **lifestyle-aligned advisory products**. | Build long-term relationships with mid-career clients who are most likely to churn. |
| **Multi-Product Customers** | Simplify product offerings and communicate benefits clearly; focus on **value alignment**, not volume. | Prevent dissatisfaction caused by product overload or unclear benefits. |
| **Customer Satisfaction** | Conduct **regular satisfaction and feedback surveys**, monitoring CSAT and NPS by region and segment. | Detect early signs of dissatisfaction and prioritize service improvements. |
| **Churn Monitoring** | Integrate the **churn prediction model** into CRM systems to flag at-risk customers in real time. | Enable proactive interventions allowing teams to act before customers disengage completely. |
| **Competitive Retention** | Continuously track **competitor offerings, pricing, and service innovations**. | Maintain market competitiveness and retain premium and mid-tier customers effectively. |


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


