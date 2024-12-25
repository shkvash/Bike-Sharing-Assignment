
# Predicting Bike Demand Using Multiple Linear Regression

## Objective

The goal of this project is to build a predictive model for shared bike demand (cnt) using multiple linear regression. The model aims to:

- Identify key factors influencing bike demand.
- Provide a robust predictive framework to support business decisions.
- Enhance understanding of demand patterns to inform strategic planning.

## Table of Contents
* [Data Overview]
* [Preprocessing Steps]
* [Exploratory Data Analysis (EDA)]
* [Modeling and Evaluation]
* [Findings]
* [Conclusions]
* [Acknowledgements]

## Data Overview

**Dataset:** Daily bike demand data provided by BoomBikes, spanning two years with 730 rows and 16 columns.

**Key Variables:**

- **Target Variable:** cnt (total bike demand).

- **Predictor Variables:**
  - **Continuous:** temp (normalized temperature), atemp (feels-like temperature), hum (humidity), windspeed (normalized wind speed).
  - **Categorical:** season (Spring, Summer, Fall, Winter), weathersit (weather condition), holiday, workingday, yr (year).

## Preprocessing Steps

- **Data Cleaning:** Dropped irrelevant columns (instant, dteday) and ensured no missing values.
- **Feature Engineering:**
  - Converted categorical variables into dummy variables.
  - Added polynomial features for continuous variables to capture non-linear relationships.
  - Scaled features to ensure uniformity across variables.
- **Multicollinearity Check:** Analyzed Variance Inflation Factor (VIF) to reduce redundancy among predictors.

## Exploratory Data Analysis (EDA)

**Key Insights:**

1. **Temperature (temp) and Bike Demand (cnt):** Strong positive correlation (≈ 0.86), indicating higher demand on warmer days.
2. **Seasonality:** Bike demand peaks during summer and fall, with lower demand in winter and spring.
3. **Weather Conditions:** Clear weather significantly boosts demand, while adverse conditions (e.g., heavy rain/snow) suppress it.
4. **Continuous Variables:** Polynomial features highlighted non-linear relationships, especially for temp and windspeed.
5. **Categorical Trends:**
   - Weekends (non-working days) show higher casual usage.
   - Registered users dominate during weekdays.

**Visualizations:**
- **Distribution Plots:** Revealed the spread and central tendencies of numerical variables.
- **Correlation Heatmap:** Identified strong correlations between temp, atemp, and cnt.
- **Scatter Plots:** Highlighted key relationships (e.g., temp vs. cnt).
- **Box Plots:** Showed seasonal and categorical variations in demand.

## Modeling and Evaluation

#### Modeling Approach

Built multiple linear regression models:

- **Ordinary Least Squares (OLS):** Baseline model to assess overall fit.
- **Ridge Regression (L2 Regularization):** To address multicollinearity and improve generalization.
- **Lasso Regression (L1 Regularization):** To perform feature selection by shrinking less important coefficients to zero.

Added polynomial features for continuous variables to enhance predictive power.

Fine-tuned hyperparameters (alpha) using cross-validation to optimize regularization strength.

Evaluated models using R² and RMSE on test data.

#### Performance Metrics

| Model   | R² (Test)   | RMSE (Test) |
|---------|-------------|-------------|
| Ridge   | -0.8795     | 2640.85     |
| Lasso   | 0.8655      | 706.39      |

## Findings

1. **Lasso Regression:**
   - Outperformed Ridge in terms of R² and RMSE, making it the preferred model for this dataset.
   - Successfully mitigated multicollinearity by excluding less significant predictors.

2. **Ridge Regression:**
   - Struggled with generalization, possibly due to overfitting or lack of effective regularization for this dataset.

3. **Polynomial Features:**
   - Enhanced model accuracy by capturing non-linear trends, especially for temp and windspeed.

## Conclusions

1. **Deploy the Lasso Model:**
   - Provides high predictive accuracy (R² = 0.8655) with minimal error (RMSE = 706.39).
   - Ideal for demand forecasting and operational planning.

2. **Business Insights:**
   - **Seasonal Focus:** Allocate more resources (e.g., bikes, staff) during high-demand seasons like summer and fall.
   - **Weather Sensitivity:** Implement flexible pricing strategies to incentivize usage during less favorable weather conditions.
   - **Targeted Marketing:** Promote services heavily on clear-weather days and weekends to maximize casual ridership.

## Acknowledgements
- This project was inspired by an upGrad live session on the industry relevance of linear regression models.
- UpGrad tutorials on Linear Regression available on the learning platform.

## Contact
Created by - [@shkvash](https://github.com/shkvash)
