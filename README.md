

This project uses the **UCI Household Power Consumption Dataset** to forecast short-term energy usage. The goal is to predict the `Global_active_power` (in kilowatts) using historical consumption and environmental features like voltage and sub-metering values.

- Source: UCI Machine Learning Repository  
- File: `household_power_consumption.txt`  
- Size was rduced to decrease stress of computation
- Features:
  - `Date` and `Time`: Combined into a datetime index
  - `Global_active_power`: Target variable (in kilowatts)
  - `Global_reactive_power`, `Voltage`, `Global_intensity`
  - `Sub_metering_1`, `Sub_metering_2`, `Sub_metering_3`

I performed hourly resampling to reduce granularity and computational load.

## Data Cleaning

- Parsed and combined `Date` and `Time` into a `datetime` index
- Converted numeric columns from strings and replaced `'?'` with NaNs
- Imputed missing values using forward fill

## Exploratory Analysis

Basic EDA was done to examine:
- Distribution of `Global_active_power`
- Trends in voltage and sub-metering across time
- Seasonality using resampling (daily/monthly)

## Model

Used a **Random Forest Regressor** to predict `Global_active_power` using other features.

### Features Used:
- `Global_reactive_power`
- `Voltage`
- `Global_intensity`
- `Sub_metering_1`
- `Sub_metering_2`
- `Sub_metering_3`

### Evaluation Metrics:

| Metric | Value |
|--------|--------|
| **MAE** (Mean Absolute Error) | `0.5381` kW |
| **RMSE** (Root Mean Squared Error) | `0.7401` kW |

These values suggest the model can predict average hourly power usage with reasonable accuracy, considering the typical household usage patterns.

## 📈 Results

- Plotted feature importances from the Random Forest model
- Visualized predicted vs actual energy usage
- Predicted trend followed the actual trend very closely suggesting that the model is accurate


