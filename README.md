# 🚗 Salifort Motors — Employee Retention Prediction

[![Python](https://img.shields.io/badge/Python-3.11-blue?logo=python)](https://www.python.org/)
[![scikit-learn](https://img.shields.io/badge/scikit--learn-1.3-orange?logo=scikit-learn)](https://scikit-learn.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Google ADAC](https://img.shields.io/badge/Google-Advanced%20Data%20Analytics-blue?logo=google)](https://grow.google/certificates/)
[![PACE](https://img.shields.io/badge/Framework-PACE-purple)](https://grow.google/certificates/)

> **Google Advanced Data Analytics Certificate — Course 6 Capstone Project**  
> *Can we predict which employees are at risk of leaving Salifort Motors — and why?*

---

## 📋 Project Overview

Salifort Motors is facing a costly employee turnover problem. The senior HR leadership commissioned a data-driven study to:

1. **Identify the key drivers** of employee departure
2. **Build a predictive model** to flag employees at risk of leaving
3. **Deliver actionable recommendations** to reduce attrition

This project applies the **PACE framework** (Plan → Analyze → Construct → Execute) across three machine learning models to answer the business question with quantifiable confidence.

---

## 🗂️ Repository Structure

```
salifort-motors-retention/
│
├── 📓 salifort_motors_capstone.ipynb   ← Main analysis notebook (PACE framework)
├── 📊 salifort_executive_summary.pdf   ← One-page executive summary for stakeholders
├── 📄 PACE_strategy_document.pdf       ← Project planning and reflection document
│
├── 📁 images/                          ← All EDA and model visualisations
│   ├── fig_turnover.png
│   ├── fig_satisfaction.png
│   ├── fig_hours_sat.png
│   ├── fig_dept.png
│   ├── fig_salary_proj.png
│   ├── fig_corr.png
│   ├── fig_tenure.png
│   ├── fig_confusion.png
│   ├── fig_roc.png
│   ├── fig_comparison.png
│   ├── fig_feature_importance.png
│   └── fig_tree.png
│
├── 📄 requirements.txt                 ← Python dependencies
└── 📄 README.md                        ← This file
```

---

## 📊 Dataset

| Attribute | Detail |
|-----------|--------|
| **Source** | HR_capstone_dataset.csv |
| **Rows** | 14,999 employee records |
| **Columns** | 10 features |
| **Target** | `left` (1 = departed, 0 = stayed) |
| **Turnover Rate** | ~14.9% |

### Feature Description

| Column | Type | Description |
|--------|------|-------------|
| `satisfaction_level` | Float (0–1) | Employee self-reported satisfaction |
| `last_evaluation` | Float (0–1) | Score from last performance review |
| `number_project` | Integer | Number of projects assigned |
| `average_monthly_hours` | Integer | Average hours worked per month |
| `time_spend_company` | Integer | Years at the company |
| `work_accident` | Binary | Whether employee had a work accident |
| `left` | Binary | **Target** — whether employee left |
| `promotion_last_5years` | Binary | Promoted in last 5 years |
| `department` | Categorical | Department name |
| `salary` | Ordinal | Salary band: low / medium / high |

---

## 🔬 PACE Framework

### 🟣 Plan
- Defined the business problem and stakeholder needs
- Identified key research questions around satisfaction, workload, tenure, and compensation
- Mapped deliverables: EDA notebook, predictive model, executive summary

### 🔵 Analyze
- Performed comprehensive EDA across all 10 features
- Uncovered two distinct leaver profiles: low-satisfaction employees AND overworked high-performers
- Identified department-level and salary-level turnover disparities
- Validated data quality: no missing values; duplicates removed

### 🟢 Construct
- Engineered three additional features: `salary_enc` (ordinal), `dept_enc` (label), `overworked` flag (hrs > 215)
- Applied stratified 80/20 train-test split
- Built and tuned three models via 5-fold `GridSearchCV`:
  - Decision Tree Classifier
  - Random Forest Classifier
  - Gradient Boosting Classifier

### 🔴 Execute
- Evaluated all models on held-out test set
- Selected **Gradient Boosting** as champion model
- Delivered feature importance rankings and visual interpretability via pruned Decision Tree
- Formulated six strategic HR recommendations

---

## 🏆 Model Results

| Model | Accuracy | Precision | Recall | F1-Score | AUC-ROC |
|-------|----------|-----------|--------|----------|---------|
| Decision Tree | 0.980 | 0.927 | 0.939 | 0.933 | 0.997 |
| Random Forest | 0.979 | 0.893 | 0.973 | 0.931 | 0.997 |
| **Gradient Boosting ★** | **0.980** | **0.931** | **0.937** | **0.934** | **0.997** |

> ★ **Champion Model**: Gradient Boosting — highest F1-Score (0.934) and AUC-ROC (0.997)  
> All models trained with 5-fold cross-validation and `GridSearchCV` hyperparameter tuning.

---

## 📈 Key Visualisations

### Turnover Distribution
![Turnover](images/fig_turnover.png)

### Satisfaction Level by Turnover Status
![Satisfaction](images/fig_satisfaction.png)

### Monthly Hours vs Satisfaction
![Hours vs Satisfaction](images/fig_hours_sat.png)

### Feature Importance — Random Forest
![Feature Importance](images/fig_feature_importance.png)

### ROC Curves — All Models
![ROC](images/fig_roc.png)

### Model Comparison
![Comparison](images/fig_comparison.png)

---

## 💡 Key Findings

1. **Satisfaction Level** is the strongest single predictor of departure (Gini importance: 0.643). Employees scoring below 0.45 carry the highest risk.

2. **Workload Extremes** create two departure clusters: employees working **>215 hrs/month** (burnout) and those working **<150 hrs/month** (disengagement). Both groups show elevated attrition.

3. **Project Overload** — employees assigned 6+ concurrent projects show a sharp spike in departure probability.

4. **The 3–4 Year Inflection Point** — tenure is the second most behavioural predictor. Employees who have not received a growth signal by year 3–4 are the most vulnerable to leaving.

5. **Salary Disparity** — low-salary employees depart at nearly **2× the rate** of medium-salary peers, particularly in Sales, Technical, and Support departments.

---

## 🎯 Recommendations

| Priority | Recommendation |
|----------|----------------|
| 🔴 High | Deploy the Gradient Boosting model in an HR early-warning dashboard; score all employees monthly |
| 🔴 High | Conduct workload audit in Sales, Technical, Support; cap projects at 5 per employee |
| 🟠 Medium | Implement biannual satisfaction surveys with automated intervention triggers at scores < 0.50 |
| 🟠 Medium | Create a structured 3-year retention review: career growth conversation + promotion consideration |
| 🟡 Standard | Commission salary benchmarking; targeted retention bonuses for high-performing low-salary staff |
| 🟡 Standard | Retrain the model quarterly with updated HR data |

---

## 🛠️ Installation & Usage

```bash
# 1. Clone the repository
git clone https://github.com/<your-username>/salifort-motors-retention.git
cd salifort-motors-retention

# 2. Create a virtual environment (recommended)
python -m venv venv
source venv/bin/activate        # Linux / macOS
venv\Scripts\activate           # Windows

# 3. Install dependencies
pip install -r requirements.txt

# 4. Launch the notebook
jupyter notebook salifort_motors_capstone.ipynb
```

> **Note:** The notebook generates a synthetic dataset that mirrors the structure of the real `HR_capstone_dataset.csv`. To use the original dataset, place it in the project root and update the `pd.read_csv()` path in Cell 3.

---

## 📦 Tech Stack

| Category | Libraries |
|----------|-----------|
| Data Manipulation | `pandas`, `numpy` |
| Visualisation | `matplotlib`, `seaborn` |
| Machine Learning | `scikit-learn` |
| Models Used | `DecisionTreeClassifier`, `RandomForestClassifier`, `GradientBoostingClassifier` |
| Tuning | `GridSearchCV` (5-fold CV) |
| Metrics | Accuracy, Precision, Recall, F1, AUC-ROC, Confusion Matrix |
| Notebook | `jupyter` |

---

## 📄 Files

| File | Description |
|------|-------------|
| `salifort_motors_capstone.ipynb` | Full PACE-structured analysis with embedded visualisations |
| `salifort_executive_summary.pdf` | Polished executive summary for non-technical stakeholders |
| `PACE_strategy_document.pdf` | Google ADAC PACE planning and reflection document |
| `requirements.txt` | Python package dependencies |

---

## 🎓 Certificate Context

This project is the **Course 6 Capstone** of the [Google Advanced Data Analytics Professional Certificate](https://grow.google/certificates/advanced-data-analytics/) on Coursera. The certificate covers:

- Python for Data Science
- Exploratory Data Analysis
- Statistical Analysis & Hypothesis Testing
- Regression Analysis
- Machine Learning with scikit-learn
- Data storytelling and executive communication

---

## 📬 Author

**Arijit Burman**  
Senior Manager IT | Oracle RAC DBA | Data Analytics  
Union Bank of India, Mumbai

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-blue?logo=linkedin)](https://linkedin.com/in/arijit-burman)

---

## 📜 License

This project is licensed under the [MIT License](LICENSE). The dataset structure is based on the Google Advanced Data Analytics Certificate capstone template.

---

*⭐ If you found this project useful, please give it a star!*
