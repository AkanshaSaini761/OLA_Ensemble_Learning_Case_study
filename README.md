# 🚗 Ola Driver Attrition Analysis Case Study

## 🏢 About Ola
Ola is one of India's largest ride-hailing companies. With high driver churn, Ola faces challenges in retention and recruitment. Understanding what makes a driver leave the company is crucial to optimize acquisition cost and maintain operational stability.

## 🎯 Objective
Build a predictive model that identifies the likelihood of driver attrition based on demographics, performance, and income. Use ensemble learning techniques and imbalanced dataset strategies to develop robust insights and recommendations.

## 📁 Dataset Overview
**Source:** [ola_driver_scaler.csv](https://github.com/AkanshaSaini761/OLA_Ensemble_Learning_Case_study/blob/main/ola_driver_scaler.csv)

| Column                  | Description |
|-------------------------|-------------|
| `MMMM-YY`              | Reporting month |
| `Driver_ID`            | Unique identifier of the driver |
| `Age`                  | Age of the driver |
| `Gender`               | 0 = Male, 1 = Female |
| `City`                 | Encoded city code |
| `Education_Level`      | 0 = 10+, 1 = 12+, 2 = Graduate |
| `Income`               | Monthly average income |
| `Date Of Joining`      | Driver's joining date |
| `LastWorkingDate`      | Driver's last working day if they left |
| `Joining Designation`  | Designation at time of joining |
| `Grade`                | Driver’s grade for that month |
| `Total Business Value` | Monthly business value (can be negative for refunds) |
| `Quarterly Rating`     | Driver's quarterly performance rating (1–5) |

## 🎯 Exploratory Goals and Methodology

- **Data Cleaning & Preprocessing**
  - Converted dates to datetime format
  - Treated missing values using **KNN imputation** (for numerical columns)
  - Aggregated multiple records per driver into one using `groupby(Driver_ID)`

- **Feature Engineering**
  - `target`: 1 if driver has a `LastWorkingDate`, else 0
  - `rating_increased`: 1 if quarterly rating increased
  - `income_increased`: 1 if income increased over time

- **Data Transformation**
  - Handled class imbalance using **SMOTE**
  - Applied **StandardScaler** to numerical features
  - One-hot encoded categorical variables

- **Modeling Techniques**
  - Ensemble Learning: **Random Forest**, **Gradient Boosting**
  - Evaluated via: **ROC AUC**, **Classification Report**, **Confusion Matrix**

## 📈 Key Insights

- **Churn Rate:** ~68% of drivers left Ola during the observed period—urgent need for retention.
- **Age Group:** Drivers aged **25–40** are most engaged; retention strategies should target this group.
- **Income Skew:** Skewed income distribution may indicate wage inequality and lower morale.
- **City-wise Churn:** Cities like **C17, C20, and C13** show elevated churn, calling for city-specific policies.
- **Tenure Impact:** Most churn occurs within **2–6 months**, with a peak at month 5—focus on early engagement.
- **Education Level:** Has minimal impact on churn—resources should focus on performance or income indicators.
- **Raise Effect:** Drivers who did **not receive raises** had higher attrition—highlighting need for incentive plans.
- **Ratings:** Low quarterly ratings strongly correlate with churn—need for coaching or training programs.
- **Income vs. Churn:** Higher income = lower churn, especially for older drivers.
- **Engagement Metrics:** Drivers with **frequent reporting** tend to stay longer.

## 📊 Final Model Evaluation

| Model                        | Precision (Class 0) | Precision (Class 1) | Recall (Class 0) | Recall (Class 1) | ROC AUC Score |
|-----------------------------|---------------------|----------------------|------------------|------------------|----------------|
| **Random Forest + SMOTE**   | 90%                 | 95%                  | 88%              | 96%              | **0.92**        |
| **Gradient Boosting**       | 88%                 | 95%                  | 89%              | 94%              | **0.92**        |
| **XGBoost**                 | 90%                 | 95%                  | 89%              | 95%              | **0.92**        |

> ✅ **Random Forest with SMOTE** performs the best, achieving high recall and precision across both classes.  
It is especially effective at correctly identifying churned drivers (Class 1), making it a strong candidate for operational deployment.

## ✅ Recommendations

1. **Targeted Retention Programs**  
   Focus on drivers aged 25–40 and within their first 2–6 months of tenure.

2. **Wage Equality & Incentives**  
   Implement regular performance-based raises to improve morale and retention.

3. **City-Focused Interventions**  
   Design regional engagement and incentive programs for high-churn cities (C17, C20, C13).

4. **Performance Coaching**  
   Offer personalized support and training for drivers with low quarterly ratings.

5. **Boost Reporting Engagement**  
   Educate drivers on how consistent reporting helps improve performance evaluations and incentives.

6. **Income Growth Pathways**  
   Design career ladders for senior drivers, especially those with high performance and loyalty.

7. **Improve Customer Feedback Scores**  
   Investigate and address negative customer experiences driving down quarterly ratings.

8. **Early Warning System**  
   Deploy predictive models in real-time to flag high-risk drivers and offer proactive support.

## 🔧 Tools & Libraries Used

- **Python**: `pandas`, `numpy`, `seaborn`, `matplotlib`
- **Modeling**: `RandomForestClassifier`, `GradientBoostingClassifier` (scikit-learn)
- **Data Imputation**: `KNNImputer`
- **Imbalance Handling**: `SMOTE` from imbalanced-learn
- **Evaluation**: `classification_report`, `roc_auc_score`, `precision_recall_curve`
- **Environment**: Jupyter Notebook

## 📄 Output Report

📎 [ola_case_study_akansha_saini.pdf](https://github.com/AkanshaSaini761/OLA_Ensemble_Learning_Case_study/blob/main/ola_case_study_akansha_saini.pdf)  
Includes all stages: EDA, feature engineering, modeling, and strategic recommendations.

