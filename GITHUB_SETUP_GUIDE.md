# GitHub Setup Guide — Salifort Motors Project

## Step-by-step instructions to publish this repo

---

### Step 1: Create a GitHub Account (if you don't have one)
Go to https://github.com and sign up.
Use a professional username — ideally: arijit-burman or arijitburman

---

### Step 2: Create a New Repository on GitHub

1. Click the green **"New"** button on your GitHub homepage
2. Fill in:
   - **Repository name:** `salifort-motors-employee-retention`
   - **Description:** `Employee retention prediction using ML (Decision Tree, Random Forest, Gradient Boosting) | Google Advanced Data Analytics Capstone`
   - **Visibility:** Public ✅ (so recruiters can see it)
   - **Add a README:** ❌ (we have our own)
3. Click **"Create repository"**

---

### Step 3: Prepare Your Local Folder

Create this folder structure on your computer:

```
salifort-motors-retention/
├── salifort_motors_capstone.ipynb
├── salifort_executive_summary.pdf
├── PACE_strategy_document.pdf
├── requirements.txt
├── README.md
├── LICENSE
├── .gitignore
└── images/
    ├── fig_turnover.png
    ├── fig_satisfaction.png
    ├── fig_hours_sat.png
    ├── fig_dept.png
    ├── fig_salary_proj.png
    ├── fig_corr.png
    ├── fig_tenure.png
    ├── fig_confusion.png
    ├── fig_roc.png
    ├── fig_comparison.png
    ├── fig_feature_importance.png
    └── fig_tree.png
```

---

### Step 4: Push to GitHub

Open terminal / Git Bash in your project folder and run:

```bash
# Initialise Git
git init

# Add all files
git add .

# First commit
git commit -m "Initial commit: Salifort Motors Employee Retention Capstone"

# Connect to your GitHub repo (replace <your-username>)
git remote add origin https://github.com/<your-username>/salifort-motors-employee-retention.git

# Push
git branch -M main
git push -u origin main
```

---

### Step 5: Add Topics/Tags to Your Repo

On GitHub, click the gear icon next to "About" and add these topics:
- `machine-learning`
- `python`
- `data-science`
- `scikit-learn`
- `employee-retention`
- `random-forest`
- `gradient-boosting`
- `google-data-analytics`
- `capstone-project`
- `hr-analytics`

---

### Step 6: Add the GitHub Link to Your LinkedIn Profile

1. Go to your LinkedIn profile → **Featured** section
2. Click **+ Add** → **Link**
3. Paste your GitHub repo URL
4. Title: "Salifort Motors Employee Retention — ML Capstone"
5. Description: "Predicting employee attrition using Decision Tree, Random Forest, and Gradient Boosting. AUC-ROC: 0.997 | Google Advanced Data Analytics Capstone"

---

### Your Final GitHub Repo URL will be:
`https://github.com/<your-username>/salifort-motors-employee-retention`

---
*Generated as part of the Google Advanced Data Analytics Certificate — Course 6 Capstone*
