# Household Power Consumption Forecasting

## Project Overview
This project analyzes the "Household Power Consumption" dataset to forecast electricity usage, specifically the *Global Active Power*, using time series forecasting and machine learning techniques. The goal is to predict power consumption for the next hour based on historical data.

## Dataset
The dataset contains measurements of electric power consumption in one household with a one-minute sampling rate over several years. It includes variables like:

- Global_active_power
- Global_reactive_power
- Voltage
- Global_intensity
- Sub_metering_1, 2, 3

Source: [UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/individual+household+electric+power+consumption)

## Data Cleaning and Preprocessing
- Loaded data from CSV with proper separator (`;`).
- Handled missing values by converting '?' to NaN and filling numeric columns with their mean.
- Converted date and time columns to a datetime index.
- Resampled data to hourly frequency by taking the mean.
- Dropped remaining missing values after conversion.

## Modeling Approaches
1. **Random Forest Regression**
   - Features: past hourly measurements of power consumption and other variables.
   - Target: next hour's Global Active Power.
   - Split data chronologically into train (80%) and test (20%).
   - Evaluated with MAE and RMSE.

2. **Prophet Time Series Forecasting**
   - Forecasted next 24 hours of Global Active Power.
   - Used Prophet for automatic trend and seasonality modeling.




