# 🚲 Factors Affecting Daily Bike Rental Demand

A statistical modeling project for DES432 Statistics & Data Modeling at Sirindhorn International Institute of Technology (SIIT), Thammasat University.

## 👥 Team Members

| Name | Student ID |
|---|---|
| Nutnapin Chongwimansin | 6622770848 |
| Supitcha Puboonterm | 6622772539 |
| Lalitpatra Kodsup | 6622780730 |

**Course:** DES432 Statistics & Data Modeling — Section 1  
**Instructor:** Asst. Prof. Dr. Pokpong Songmuang

---

## 📋 Project Overview

This project investigates whether weather-related variables are statistically associated with daily bike rental demand in Washington D.C. Using the [UCI Bike Sharing Dataset](https://archive.ics.uci.edu/ml/datasets/Bike+Sharing+Dataset) (`day.csv`), we build and compare a simple and a multiple linear regression model to explain and predict daily rental counts.

**Research Question:** Are temperature, humidity, and wind speed statistically associated with daily bike rental demand?

---

## 📊 Dataset

- **Source:** [UCI Machine Learning Repository — Bike Sharing Dataset](https://archive.ics.uci.edu/ml/datasets/Bike+Sharing+Dataset)
- **Coverage:** January 1, 2011 – December 31, 2012 (Washington D.C.)
- **Observations:** 731 daily records

### Variables Used

| Variable | Role | Description |
|---|---|---|
| `cnt` | Response (Y) | Total daily bike rentals (casual + registered) |
| `temp` | Predictor (X₁) | Normalized temperature |
| `hum` | Predictor (X₂) | Normalized humidity |
| `windspeed` | Predictor (X₃) | Normalized wind speed |

> **Note:** `atemp` was excluded to avoid multicollinearity with `temp`. `casual` and `registered` were excluded to prevent data leakage.

---

## 🔬 Methodology

### 1. Exploratory Data Analysis (EDA)
- Summary statistics for all selected variables
- Distribution histogram of daily rentals (`cnt`)
- Scatterplots of each predictor vs. `cnt`
- Correlation heatmap

### 2. Hypothesis Testing
- t-test for regression coefficients (α = 0.05)
- Tested for each predictor in both simple and multiple regression settings

### 3. Modeling
- **Model 1:** Simple Linear Regression — `cnt ~ temp`
- **Model 2:** Multiple Linear Regression — `cnt ~ temp + hum + windspeed`

### 4. Model Evaluation
- R-squared and Adjusted R-squared
- MSE, RMSE, MAE
- Residual vs. Fitted plot
- Residual distribution histogram

---

## 📈 Key Results

### Regression Equations

**Model 1 (Simple):**
```
cnt = 1214.64 + 6640.71 × temp
```

**Model 2 (Multiple):**
```
cnt = 4084.36 + 6625.53 × temp − 3100.12 × hum − 4806.93 × windspeed
```

### Model Comparison

| Model | Predictors | R² | Adj. R² | RMSE | MAE |
|---|---|---|---|---|---|
| Model 1 | `temp` | 0.3937 | 0.3929 | 1507.32 | 1246.36 |
| Model 2 | `temp`, `hum`, `windspeed` | 0.4609 | 0.4587 | 1421.40 | 1164.15 |

**Model 2 is selected as the final model** — it explains more variance and produces lower prediction errors.

### Hypothesis Testing Summary

All three predictors were found to be statistically significant (p < 0.05) in the multiple regression model:

| Predictor | t-statistic | p-value | Decision |
|---|---|---|---|
| `temp` | 22.61 | 4.18 × 10⁻⁸⁶ | Reject H₀ |
| `hum` | −8.07 | 2.83 × 10⁻¹⁵ | Reject H₀ |
| `windspeed` | −6.78 | 2.48 × 10⁻¹¹ | Reject H₀ |

---

## 💡 Key Insights

- **Temperature** is the strongest predictor: higher temperatures are associated with more rentals (r ≈ 0.63).
- **Humidity** and **windspeed** both have weak negative associations with rentals, but are statistically significant when combined in the multiple regression model.
- The final model explains about **46%** of the daily variation in bike rentals — a meaningful improvement over temperature alone (39%), though substantial unexplained variance remains.
- Results reflect **statistical associations**, not causation, as the dataset is observational.

---

## ⚙️ How to Run

### Requirements

```bash
pip install pandas numpy matplotlib seaborn scipy statsmodels scikit-learn
```

### Steps

1. Clone this repository
2. Place `day.csv` inside the `data/` folder
3. Open `pokpong_final_ver.ipynb` in Jupyter Notebook or JupyterLab
4. Run all cells from top to bottom

---

## ⚠️ Limitations

- Observational data — results show association, not causation
- Only three predictors used; season, holiday, and working-day effects were not included
- Predictors are normalized, so coefficients reflect scaled-unit changes
- In-sample error metrics only — no train/test split or cross-validation was applied
- Daily time-series data may violate the independence assumption



"# DES432_Project2_Factors-Affecting-Daily-Bike-Rental-Demand" 
