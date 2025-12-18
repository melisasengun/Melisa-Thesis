# Short-Term Retail Demand Forecasting for Inventory Decisions

## Demand Forecasting of Retail Sales (Aggregated Daily)
This repository contains the entire implementation of the demand forecasting task pipeline as developed for the Master’s thesis project. The task of analysis aims at estimating the overall daily aggregated retail demand by applying classical methods of time series, as well as a machine learning approach, while being consistent in methodology between the statistical and machine learning methods.

## Dataset Overview
The study is based on the synthetic retail data that simulates real-world data characteristics. The original dataset contains approximately **73,100 transactional observations**, where each row represents the sales activity of a specific product in a specific store on a given day (store–product–day level).

To use this data for forecasting, it is aggregated to a daily level, giving one time series with 731 observations covering January 2022 to January 2024.

The combined data is divided chronologically in the following manner:
- Training set: 584 days (first 80%)
- Test set: 147 days (remaining 20%)

 The major considerations include pricing, promotions, competitive pricing, season, calendar variables, and weather conditions.

## Repository Structure

Data
- retail_store_inventory.csv (Synthetic transactional retail dataset)

notebook
- Thesis_codes-3.ipynb (Main Jupyter Notebook: EDA, modeling, evaluation)

README.md (Project documentation)




The notebook follows a structured and time-consistent forecasting pipeline:

1. Data loading and validation  
2. Exploratory Data Analysis (EDA)  
3. Daily aggregation of transactional data  
4. Baseline forecasting using a Naïve method  
5. Time series modeling using SARIMA  
6. Machine learning modeling using CatBoost  
7. Model evaluation and comparison using MAE, RMSE, and MAPE  

All models are trained and evaluated using a **time-ordered train–test split** to prevent information leakage.


## Models Implemented

### Naive Benchmark

The simplest form of a baseline forecasting method would be to assume that the demand on a given day is identical to that on the preceding day. This acts as a benchmark.

### SARIMA

A Seasonal ARIMA model is used to capture the dependency in the data for the aggregated daily demand series. The mechanism of the Seasonal ARIMA model includes the effect of seasonality and acts as a classical statistical benchmark.

### CatBoost Regressor

A gradient boosting regression model is applied utilizing CatBoost. The model employs the numerical aggregated features, calendar features, and chosen categorical features. The categorical features like Weather Condtion and Seasonality are taken care of by CatBoost itself through an in-built encoding system, which makes encoding and normalization unnecessary. 

**Feature availability assumption:** In the CatBoost model, all the variables that are used as an explanation (prices, promotions, weather, and calendar variables) are presumed to be either available or forecastable during the prediction task.

## Evaluation Metrics

Model performance is assessed using three complementary error metrics:
- Mean Absolute Error (MAE)
- Root Mean Squared Error (RMSE)
- Mean Absolute Percentage Error (MAPE)

Using multiple metrics enables a balanced evaluation of absolute accuracy, sensitivity to large errors, and relative forecasting performance.

## Reproducibility

- The notebook is executed in **Google Colab**
- All required libraries are imported within the notebook


## Author

**Melisa Sengun**  
MSc in IT for Business Data Analytics  














