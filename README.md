# dev-salary-predictor

> Predict your developer salary based on country, role, years of experience, and tech stack — trained on 48,000+ Stack Overflow survey responses.

![Python](https://img.shields.io/badge/Python-3.8%2B-blue?style=flat-square)
![scikit-learn](https://img.shields.io/badge/scikit--learn-GradientBoosting-orange?style=flat-square)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?style=flat-square)
![License](https://img.shields.io/badge/License-MIT-green?style=flat-square)

---

## Overview

This project uses a **Gradient Boosting** machine learning model to predict annual developer salaries in USD. It was built from the [Stack Overflow Developer Survey](https://survey.stackoverflow.co/) dataset (~48,000 responses) and features an interactive input interface where you can enter your own profile and get a salary estimate instantly.

**Model performance:**
- R² score: ~0.64 (explains 64% of salary variance)
- Median prediction error: ~25%
- Training data: 43,000+ developers across 30+ countries

---

## Features

- Gradient Boosting Regressor (non-linear, handles feature interactions)
- Log-transformed salary target for more accurate predictions across income ranges
- 80+ features: country, dev role, education, experience, 15+ languages, cloud platforms, databases, DevOps tools, and frameworks
- Two prediction modes: interactive Q&A prompts or edit-a-dict quick mode
- Model saved to `salary_model.pkl` — no retraining needed on reuse
- Full EDA with charts: salary distribution, feature importance, error by salary range

---

## Project structure

```
dev-salary-predictor/
├── Salary_predicting_improved.ipynb   # Main notebook (EDA + training + predictor)
├── survey_results_slim.csv            # Dataset (Stack Overflow Survey)
├── salary_model.pkl                   # Saved model (generated after first run)
├── requirements.txt
└── README.md
```

---

## Quick start

### 1. Clone the repo

```bash
git clone https://github.com/YOUR_USERNAME/dev-salary-predictor.git
cd dev-salary-predictor
```

### 2. Install dependencies

```bash
pip install -r requirements.txt
```

### 3. Launch the notebook

```bash
jupyter notebook Salary_predicting_improved.ipynb
```

Run all cells top to bottom. Training takes ~60 seconds. Once complete, jump to **Section 9 or 10** to get your salary prediction.

---

## How to predict your salary

### Option A — Interactive (Section 9)
Run the cell and answer the numbered prompts: country, role, education, experience, and tech stack yes/no questions.

### Option B — Quick dict (Section 10)
Edit the `inputs = dict(...)` block directly with your values and run the cell. No prompts, instant output.

**Example output:**
```
  Role:     Full-stack developer
  Country:  Canada
  Exp:      5 years

  Predicted Salary:   $92,400 / year (USD)
  Likely Range:       $69,300  –  $115,500
```

---

## Why Gradient Boosting over Linear Regression

Linear regression assumes salary is a simple additive sum of features — it can't capture that a senior Rust + Kubernetes + AWS developer earns *disproportionately* more than the parts suggest. Gradient Boosting builds hundreds of decision trees that learn those interaction effects directly.

| Metric | Linear Regression | Gradient Boosting |
|---|---|---|
| R² (test) | ~0.35 | ~0.64 |
| MAE | ~$35,000 | ~$28,000 |
| Countries | 15 | 30+ |
| Dev types | 10 | 15+ |

---

## Dataset

- **Source:** Stack Overflow Developer Survey 2024
- **Size:** 48,019 responses → 43,407 after cleaning
- **Salary filter:** $10,000–$500,000 USD/year (removes data entry errors and extreme outliers)
- The CSV is included in this repo for reproducibility.

---

## Limitations

- All salaries are in **USD** — use a currency converter for local equivalents
- Predictions are only as good as the survey sample (self-reported, English-speaking developer community skew)
- "Other" country predictions are weaker — the model has less data for smaller countries
- The model does not account for cost of living

---

## License

MIT — see [LICENSE](LICENSE) for details.

---

## Author

Built by Ahmed as part of a data science project.
