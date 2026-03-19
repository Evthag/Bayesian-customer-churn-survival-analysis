# Bayesian Customer Churn Survival Analysis

Bayesian survival analysis pipeline built with PyMC, modelling time-to-churn on the IBM Telco Customer Churn dataset. Goes beyond standard churn classification by treating churn as a time-to-event problem — properly handling censored observations (customers who haven't churned yet) and quantifying uncertainty across all estimates.

---

## Models

| Model | Type | Key Feature |
|-------|------|-------------|
| Exponential | Parametric | Constant hazard rate baseline |
| Weibull | Parametric | Time-varying hazard via shape parameter α |
| Cox Proportional Hazards | Semi-parametric | Covariate effects on survival time |

All three models are compared using WAIC and LOO-CV via ArviZ.

---

## Outputs

- **Survival curves** — posterior predictive S(t) with 95% credible intervals vs Kaplan-Meier empirical baseline
- **Hazard plots** — h(t) across all three models
- **Trace plots** — MCMC diagnostics and posterior distributions for all parameters
- **Covariate effects** — forest plot of Cox PH hazard ratios with credible intervals
- **Model comparison** — WAIC/LOO table and ArviZ compare plot

---

## Key Findings

- Contract type is the strongest protective factor — two-year contracts dramatically reduce churn hazard
- Higher monthly charges increase churn risk
- Tech support availability is protective
- Weibull α < 1 indicates decreasing hazard — early-tenure customers are most at risk


## Dataset

[IBM Telco Customer Churn](https://www.kaggle.com/datasets/blastchar/telco-customer-churn) — 7,043 telecom customers with tenure, contract type, service features, and churn status.
