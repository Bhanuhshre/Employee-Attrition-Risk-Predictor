# Employee-Attrition-Risk-Predictor
Developed an XGBoost classifier with SHAP explainability on 1,470 IBM HR records, achieving 89\% recall across 35 features. Developed a Streamlit application that visualized attrition risk scores and key contributing factors for employee retention analysis.

## What this project does

- Loads and cleans the IBM HR dataset
- Does exploratory data analysis with 13 visualizations
- Engineers 4 new features based on business logic
- Trains an XGBoost classifier to predict attrition
- Uses SHAP values to explain which features matter the most
- Achieves 89% recall on the test set

---

## Dataset

- Source: IBM HR Analytics Employee Attrition and Performance
- Records: 1,470 employees
- Features: 35 (dropped 3 constant columns)
- Target: Attrition (Yes / No) — 16.1% attrition rate

---

## Tech Stack

- Python 3.x
- pandas, numpy
- matplotlib, seaborn
- scikit-learn
- XGBoost
- SHAP

---

## Project Structure

```
IBM-HR-Attrition/
│
├── IBM_HR_Attrition_XGBoost_SHAP.ipynb   # Main notebook
├── WA_Fn-UseC_-HR-Employee-Attrition.csv  # Dataset
└── README.md
```

---

## How to run

1. Clone the repository

```
git clone https://github.com/your-username/ibm-hr-attrition.git
cd ibm-hr-attrition
```

2. Install the required libraries

```
pip install pandas numpy matplotlib seaborn scikit-learn xgboost shap
```

3. Open the notebook

```
jupyter notebook IBM_HR_Attrition_XGBoost_SHAP.ipynb
```

---

## Notebook Sections

1. Library Imports and version check
2. Data Loading
3. Data Understanding (dtypes, missing values, duplicates, statistics)
4. Data Cleaning
5. Exploratory Data Analysis (8+ charts)
6. Feature Engineering (4 new features)
7. Model Building (Baseline and Tuned XGBoost)
8. Model Evaluation (Confusion Matrix, ROC Curve, Feature Importance)
9. SHAP Explainability (Global bar plot and Beeswarm plot)
10. Business Insights
11. Recommendations
12. Final Results Summary

---

## Model Results

| Metric    | Score  |
|-----------|--------|
| Accuracy  | 86.39% |
| Recall    | 89.36% |
| Precision | 54.90% |
| F1-Score  | 67.97% |
| ROC-AUC   | 0.9312 |

I prioritized recall here because in an HR context it is more important to catch employees who are about to leave rather than worrying about false positives.

---

## Key Findings

- Employees who do overtime have about 30% attrition rate vs 10% for those who don't
- Employees who left had a much lower median salary (around $3.2K vs $5.3K)
- Sales Representatives have the highest attrition rate at nearly 40%
- Employees with no stock options are 3x more likely to leave
- Single employees leave more often than married or divorced employees
- New employees (0 to 2 years) are at the highest risk

---

## Feature Engineering

I created 4 new features that made the model better:

- **IncomeToAgeRatio** — monthly income divided by age, shows how fast someone is progressing in their career
- **TenureRatio** — years at the company divided by total working years, shows loyalty
- **YearsSincePromotion_Adj** — promotion gap multiplied by overtime status, acts as a burnout indicator
- **SatisfactionScore** — average of job satisfaction, environment satisfaction, relationship satisfaction, and work-life balance

---

## SHAP Explainability

I used SHAP (SHapley Additive exPlanations) to understand what the model is learning. The top features driving attrition according to SHAP are:

1. MonthlyIncome
2. OverTime
3. SatisfactionScore
4. StockOptionLevel
5. Age

---

## Acknowledgements

- Dataset from IBM via Kaggle
- SHAP library by Scott Lundberg
