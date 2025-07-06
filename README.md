# Forecasting Road Accident Numbers in Saudi Arabia Using AI-Based Time-Series Models

## Project Overview
This project uses AI-based time-series models to forecast monthly traffic deaths and injuries in Saudi Arabia. The goal is to support proactive road safety planning by predicting future accident outcomes using historical government-reported data.

## Dataset
- **Source:** Saudi Open Data Platform
- **Files Used:**
  - Injured and Dead in Accidents 1437 H
  - Injured and Dead in Accidents 1438 H
  - Injured and Dead in Accidents 1439 H
- **Size:** 1152 rows, 20 columns

### Key Features
- Temporal: gregorian_year, gregorian_month, gregorian_day
- Region: region_number
- Demographics: male_count, female_count, age groups, nationality counts
- Targets: total_deaths, total_injuries
- Lag features: deaths_lag1, injuries_lag1 (engineered)

## Data Preprocessing
- Combined multiple files (each file contained separate sheets for deaths and injuries) into a single dataframe
- Added total_deaths, total_injuries, and year columns
- Dropped region_name and month_name, replaced with region_number and month_number
- Converted Hijri dates to Gregorian dates
- Created lag features (deaths_lag1, injuries_lag1) for temporal modeling

## Exploratory Data Analysis (EDA)
- Checked data structure, types, and missing values
- Reviewed summary statistics
- Generated heatmaps to explore correlations
- Plotted yearly and monthly trends to identify seasonality
- Compared deaths and injuries across regions
- Visualized demographic distributions
- Created animated plots to show changes over time by region

## Models Used
- CatBoost Regression: good for structured tabular data with minimal preprocessing
- LightGBM Regression: used with time-series cross-validation; outperformed CatBoost in all tasks

## Results
**CatBoost**
- Deaths Prediction: R² = 0.76 (with injuries_lag1), drops to 0.38 without it
- Injuries Prediction: R² = 0.77 (with deaths_lag1), drops to 0.47 without it

**LightGBM**
- Deaths Prediction: R² = 0.95, MAE = 3.31, RMSE = 6.32
- Injuries Prediction: R² = 0.96, MAE = 12.09, RMSE = 23.83

## Key Insights
- Lag features are crucial predictors, reflecting temporal patterns
- Region number shows consistent importance
- LightGBM performed best overall

## Future Work
- Integrate external features such as traffic volume, weather, and enforcement data

## Tools Used
Python, pandas, scikit-learn, CatBoost, LightGBM, matplotlib, seaborn, Plotly, GPT-4
