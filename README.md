# COVID-19 Vaccination Forecasting (Bangladesh, India, Pakistan)

Comparative time-series forecasting study of COVID-19 cumulative vaccination trajectories for three South Asian countries using ARIMA, SARIMA, and Hidden Markov Models (HMM).  
*CSE427 — Time Series Forecasting*

---

## Overview

This project evaluates how well three model families forecast daily cumulative vaccination counts 180 days ahead. Models are compared against each other and against a naïve persistence baseline using four error metrics and Diebold-Mariano significance tests.

**Countries:** Bangladesh · India · Pakistan  
**Data:** [Our World in Data COVID-19 dataset]([https://github.com/owid/covid-19-data](https://www.kaggle.com/datasets/caesarmario/our-world-in-data-covid19-dataset)) (`owid-covid-data.csv`)  
**Forecast horizon:** 180 days  
**Train/test split:** 80 / 20 (temporal, no shuffle)

---

## Models

| Model | Order selection | Notes |
|---|---|---|
| ARIMA | AIC via `auto_arima` | d=1, non-seasonal |
| SARIMA | AIC via `auto_arima` | d=1, D=1, m=7 (weekly) |
| HMM | BIC sweep (2–12 components) | Gaussian emissions, diagonal covariance |
| Naïve baseline | — | Last training value repeated across test set |

---

## Evaluation

- Metrics: MAE, MSE, RMSE, MAPE
- Statistical comparison: two-sided Diebold-Mariano test (squared-error loss) for every model pair including vs. naïve baseline
- 95% prediction intervals reported for ARIMA and SARIMA future forecasts

