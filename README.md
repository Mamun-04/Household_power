# Household Power Consumption Forecasting

Project Overview

This project analyzes the "Household Power Consumption" dataset to forecast electricity usage, specifically the Global Active Power, using both classical machine learning and time series forecasting techniques. The aim is to predict power consumption and compare the effectiveness of two models:
- Random Forest Regressor
- Prophet


 Dataset

- Collected from a single household, recorded **once per minute** over several years.
- Key features:
  - `Global_active_power` (target)
  - `Global_reactive_power`
  - `Voltage`
  - `Global_intensity`
  - `Sub_metering_1`: Kitchen appliances
  - `Sub_metering_2`: Laundry appliances
  - `Sub_metering_3`: Water heater & AC

Source: [UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/individual+household+electric+power+consumption)

---

## 🧹 Data Cleaning & Preprocessing

- Parsed `Date` and `Time` into a combined `Datetime` column.
- Converted `?` to NaN and ensured all columns were numeric.
- Removed rows with missing values.
- Resampled from minute-level to hourly frequency using `.resample('H').mean()`.
- Created lag features and shifted target for machine learning forecasting.

---

Modeling Approaches:

1. Random Forest Regressor
- Features: All hourly measurements including lags (e.g., last 6 hours of `Global_active_power`).
- Target: `Global_active_power` for the next hour.
- Split: Chronologically into 80% train / 20% test.
- Evaluation:
  - MAE: `0.392`
  - RMSE: `0.543`
- Feature Importance visualized with a bar chart.

2. Use of prophet
- Forecasted next 24 hours based only on `Global_active_power`.
- Automatically modeled:
  - Trend
  - Daily seasonality
 
  


 
Model Performance Comparison:

| Model           | MAE     | RMSE    |
|------------------|----------|----------|
| Random Forest     | 0.3923   | 0.5428   |
| Prophet           | 0.3702   | 0.4868   |

Prophet outperformed Random Forest slightly in RMSE and is better at seasonality analysis


We were able to plot:

- Actual vs Predicted power usage over 24 hours for both models
- Feature correlation heatmap
- Feature importance (Random Forest)
- Prophet’s component plots (trend, daily cycles)


Improvements would be to:

- Add holiday effects to Prophet that may not be picked up by the monthly trend.
- Train on longer history and forecast multi-hour windows.
- Forecast on specific zones based on the sub-meterings




