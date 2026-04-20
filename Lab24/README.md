# Chapter 24 Lab: Double Machine Learning (DML)

**Course:** [Your Course Name]
**Author:** [Your Name]
**Date:** [Your Date]

---

## Overview

This lab applies **Double Machine Learning (DML)** to estimate the causal effect of 401(k) eligibility on household net financial assets. Using the Chernozhukov & Hansen (1991 SIPP) dataset of 9,915 households, we demonstrate why naïve ML fails for causal inference, implement the DML Partially Linear Regression model, and estimate heterogeneous treatment effects across income groups.

---

## Key Results

### Overall ATE (Average Treatment Effect)
| Metric | Value |
|--------|-------|
| DML ATE Estimate | ~$9,000 |
| 95% Confidence Interval | [$6,500 – $11,500] |
| Naïve difference-in-means | ~$19,000 (confounded) |
| Confounding bias removed | ~$10,000 |

> 401(k) eligibility causally increases net household financial assets by approximately $9,000 after controlling for income, age, education, and other confounders using machine learning.

### CATE by Income Quartile
| Income Quartile | CATE Estimate | Interpretation |
|----------------|---------------|----------------|
| Q1 (Lowest) | ~$3,500 | Small effect — liquidity constraints bind |
| Q2 | ~$6,800 | Moderate effect |
| Q3 | ~$10,200 | Above-average effect |
| Q4 (Highest) | ~$15,000 | Largest effect — tax benefits most valuable |

> The 401(k) program disproportionately benefits higher-income households, pointing toward the need for auto-enrollment and expanded Saver's Credit refundability for lower-income workers.

---

## Repo Structure

├── notebooks/
│   └── lab-ch24-guided.ipynb     # Main lab notebook (all 16 cells)
├── figures/
│   ├── part1_regularization_bias.png
│   ├── part2_eda.png
│   ├── part3_cate.png
│   ├── extension_sensitivity.png
│   ├── extension_ovb.png
│   └── ai_expansion_dashboard.png
└── README.md

---

## How to Run

### Option A: Google Colab (no setup required)
1. Go to [colab.research.google.com](https://colab.research.google.com)
2. File → Upload Notebook → select `lab-ch24-guided.ipynb`
3. Run cells top-to-bottom with **Shift+Enter**

### Option B: VS Code (recommended)
1. Clone this repo: `git clone [your-repo-url]`
2. Open `notebooks/lab-ch24-guided.ipynb` in VS Code
3. Select your Python environment (top-right kernel picker)
4. Run cells with **Shift+Enter**

### Install dependencies
```bash
pip install doubleml scikit-learn pandas numpy matplotlib seaborn statsmodels
```

---

## Lab Structure

| Part | Topic | Type | Time |
|------|-------|------|------|
| Part 1 | Regularization Bias Demo — why naïve ML fails | GUIDED | 10 min |
| Part 2 | DML on 401(k) data — setup, nuisance learners, fit | YOUR TASK | 10 min |
| Part 3 | CATE by income quartile — heterogeneous effects | YOUR TASK | 10 min |
| Extension | Sensitivity Analysis — robustness checks | OPTIONAL | 15 min |
| AI Expansion | Interactive CATE dashboard + policy memo | AI CO-PILOT | 15 min |

---

## Key Concepts

**Regularization Bias** — ML models shrink all coefficients toward zero for prediction accuracy, which biases treatment effect estimates in causal inference settings.

**Double ML (DML)** — Residualizes both Y and D on X using flexible ML, then regresses outcome residuals on treatment residuals. The "double" removes confounding from both sides simultaneously.

**Cross-Fitting** — Trains nuisance models on one fold and predicts on the held-out fold, preventing overfitting bias from contaminating the causal estimate. Analogous to cross-validation but for causal inference.

**CATE** — Conditional Average Treatment Effect. How the causal effect varies across subgroups. Estimated here by fitting separate DML models within each income quartile.

---

## References

- Chernozhukov, V., Chetverikov, D., Demirer, M., Duflo, E., Hansen, C., Newey, W., & Robins, J. (2018). Double/debiased machine learning for treatment and structural parameters. *The Econometrics Journal*, 21(1), C1–C68.
- Chernozhukov, V. & Hansen, C. (2004). The effects of 401(k) participation on the wealth distribution. *Review of Economics and Statistics*, 86(3), 735–751.
- DoubleML Python package: [docs.doubleml.org](https://docs.doubleml.org)
