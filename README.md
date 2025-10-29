#  Team Efficiency Prediction using Machine Learning

This project predicts the **operational efficiency of manufacturing teams** in a garment production unit using multiple machine learning models — Linear Regression, Random Forest, and XGBoost.  
The goal is to understand which factors most influence daily productivity and to build a model that can accurately estimate team efficiency based on operational data.

---

##  Project Overview

Manufacturing units collect daily data about team performance — such as target efficiency, idle time, worker count, overtime, and work-in-progress (WIP).  
By analyzing these factors, management can:
- Identify productivity bottlenecks
- Optimize workforce allocation
- Improve production planning

This project uses statistical analysis and machine learning to **predict efficiency scores** and uncover key operational insights.

---

##  Dataset Description

**Dataset Name:** Manufacturing Team Efficiency Dataset  
**Records:** 1,197 rows  
**Target Variable:** `efficiencyScore` (actual achieved productivity)

| Column Name | Description |
|--------------|-------------|
| `recordDate` | Date of observation |
| `fiscalQuarter` | Quarter of the fiscal year (Q1–Q4) |
| `productionDept` | Department name (e.g., Sewing, Cutting, Finishing) |
| `dayOfWeek` | Day of the week |
| `team` | Team ID or production line name |
| `plannedEfficiency` | Planned target efficiency for the day |
| `standardMinuteValue` | Standard time to produce one unit |
| `workInProgress` | Units currently being processed |
| `overtimeMinutes` | Extra time worked beyond regular hours |
| `performanceBonus` | Incentive or bonus amount |
| `idleMinutes` | Total idle time due to downtime |
| `idleWorkers` | Number of idle workers |
| `styleChangeCount` | Number of garment style changes in a day |
| `workerCount` | Total number of active workers |
| `efficiencyScore` | Actual achieved team efficiency (Target) |

---

##  Data Preprocessing

- **Handled missing values:**  
  - All missing `workInProgress` values were filled using the **median**, since all values in the *Finishing* department were null.

- **Feature Engineering:**
  - Extracted `month`, `day`, and `is_weekend` from `recordDate`
  - Encoded categorical columns using **Label encoding**
  - Scaled numerical features using **StandardScaler**

---

##  Models and Performance

| Model | Train R² | Test R² | Test RMSE | Comments |
|--------|-----------|----------|-----------|-----------|
| **Linear Regression (Standardized)** | 0.815 | 0.706 | 0.072 | Strong baseline, good generalization |
| **Random Forest** | 0.978 | 0.773 | 0.063 | Non-linear patterns captured well |
| **XGBoost (Tuned)** | 0.999 | 0.749 | 0.067 | High accuracy, stable performance |

---

##  Hyperparameter Tuning

###  Random Forest (GridSearchCV)
```python
{
  'n_estimators': [50, 100, 200],
  'max_depth': [None, 5, 10, 20],
  'min_samples_split': [2, 5, 10],
  'min_samples_leaf': [1, 2, 4],
  'max_features': ['auto', 'sqrt', 'log2']
} #  Team Efficiency Prediction using Machine Learning

This project predicts the **operational efficiency of manufacturing teams** in a garment production unit using multiple machine learning models — Linear Regression, Random Forest, and XGBoost.  
The goal is to understand which factors most influence daily productivity and to build a model that can accurately estimate team efficiency based on operational data.

 XGBoost (Best Parameters)
{
  'subsample': 1.0,
  'reg_lambda': 1,
  'reg_alpha': 0,
  'n_estimators': 400,
  'max_depth': 7,
  'learning_rate': 0.05,
  'gamma': 0,
  'colsample_bytree': 0.8
}


 Final Insights

Planned Efficiency and Worker Count were strong positive predictors of actual efficiency.

Idle Minutes and Style Changes negatively affected productivity.

Departments like Sewing showed higher variability in efficiency due to workload diversity.

Weekend shifts or overtime had mixed impacts depending on department type.

XGBoost and Random Forest both achieved strong generalization — suitable for operational forecasting.



 Key Learnings

Data preprocessing (handling missing WIP) significantly improved performance.
Feature scaling benefited linear models .
Hyperparameter tuning using GridSearchCV boosted R² by ~10–15%.
Ensemble models outperform linear models for non-linear manufacturing data.



 Technologies Used

Python 3.10+

Pandas, NumPy – Data handling

Matplotlib, Seaborn – Visualization

Scikit-learn – Preprocessing & ML models

XGBoost – Gradient boosting model

Google Colab – Cloud notebook environment



 Author
Aryan Tyagi
📧 Email: at9120140@gmail.com
🔗 GitHub: https://github.com/aryantyagi0

 Conclusion
This project demonstrates how machine learning can effectively predict team efficiency in a manufacturing environment.
It helps management make data-driven decisions to optimize productivity, reduce idle time, and plan resources efficiently.


--
