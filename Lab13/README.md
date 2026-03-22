# The Architecture of Dimensionality: Hedonic Pricing & the FWL Theorem

## Objective
Estimate a multivariate hedonic pricing model on 2026 California real estate data and formally prove the Frisch-Waugh-Lovell (FWL) theorem by manually isolating pure, uncorrelated coefficient estimates through sequential residual extraction.

---

## Tech Stack
| Tool | Role |
|---|---|
| `pandas` | Data ingestion and feature engineering |
| `statsmodels.formula.api` | OLS regression modeling |
| `matplotlib` / `plotly` | Static and interactive visualization |
| Python 3.10+ | Runtime environment |

**Dataset:** Zillow synthetic California market data (2026) — features: `Sale_Price`, `Property_Age`, `Distance_to_Tech_Hub`

---

## Methodology

- **Baseline Bivariate Regression** — Fit a naive OLS model regressing `Sale_Price` on `Property_Age` alone to establish the contaminated, omitted-variable-biased benchmark coefficient.

- **Multivariate Expansion** — Introduced `Distance_to_Tech_Hub` as a confounder control variable, extending the regression hyperplane into three-dimensional feature space and allowing the algorithm to partition variance across both predictors simultaneously.

- **FWL Theorem — Manual Execution (3-Step Proof)**
  1. Regressed `Sale_Price` on `Distance_to_Tech_Hub`; extracted price residuals (variance in price *unexplained* by location).
  2. Regressed `Property_Age` on `Distance_to_Tech_Hub`; extracted age residuals (variance in age *unexplained* by location).
  3. Regressed price residuals on age residuals with the intercept suppressed (`-1`), yielding the FWL-isolated coefficient for `Property_Age`.

- **Epistemological Verification** — Confirmed the FWL coefficient matches the multivariate OLS coefficient for `Property_Age` to multiple decimal places, proving algebraic equivalence.

---

## Key Findings

In the 2026 California market, `Property_Age` and `Distance_to_Tech_Hub` are negatively correlated: older housing stock clusters near high-value coastal tech hubs (San Francisco, San Jose)
