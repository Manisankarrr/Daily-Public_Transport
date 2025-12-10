# Time Series Forecasting of Daily Public Transport Journeys

## 1. Dataset Overview

This project analyzes daily public transport passenger counts across multiple service types such as Local Route, Light Rail, Rapid Route, School, and others.

- The raw data was cleaned and converted into a continuous daily time series.
- All service types were aggregated into a single target variable: total_journeys.
- The dataset spans multiple years and exhibits strong weekly seasonality.

## 2. Forecasting Model Used

### Prophet Model

Prophet was selected as the final forecasting model because it:

- Automatically models weekly seasonality
- Handles trend and seasonal patterns effectively
- Produces interpretable components and stable predictions

### Why SARIMAX Did Not Fit Well

SARIMAX was tested earlier but showed weaker performance due to:

- Difficulty capturing sharp weekday–weekend shifts
- Limited flexibility in modeling non-linear seasonal patterns
- Higher forecast error compared to Prophet

Prophet outperformed SARIMAX in stability and overall accuracy.

## 3. Model Performance & Evaluation

### Evaluation Metrics Used

- MAE (Mean Absolute Error)
- RMSE (Root Mean Squared Error)

### Baseline Result (before cleaning)

- Baseline MAE: 22749.25

### SARIMAX Result

- SARIMAX MAE: 14703.75

### Prophet Result

- Prophet MAE: 14273.84
- Prophet RMSE: 22307.92

## 4. Key Insights

### Insight 1: Initial Baseline Was High

The early baseline MAE (22k+) highlighted missing dates and irregularities.
<img width="1373" height="195" alt="baseline" src="https://github.com/user-attachments/assets/03ac5831-7d93-4a59-8666-79fa2ddb6559" />

### Insight 2: Prophet Delivered the Most Stable Performance

Prophet achieved the lowest MAE among tested models.  
<img width="1376" height="197" alt="prophet" src="https://github.com/user-attachments/assets/b2043ca6-ee6e-4b6c-928b-cf6343959ff3" />


### Insight 3: SARIMAX Struggled With Weekly Seasonality

Large weekend drops were not captured well, leading to higher error.  
<img width="1431" height="208" alt="sarimax" src="https://github.com/user-attachments/assets/05049a5a-1dce-4510-9c13-65975d5dc624" />


### Insight 4: Weekly Seasonality Is the Dominant Pattern

Most variation comes from weekday peaks and weekend dips, not long-term trend.  
<img width="1174" height="400" alt="image" src="https://github.com/user-attachments/assets/7d36fe07-8ee9-4c9f-9b82-159847a5fba3" />


### Insight 5: Prophet Offers Clear Decomposition for Interpretation

Trend, weekly pattern, and residuals are easy to visualize and communicate.  

## 5. Exploratory Data Analysis (EDA)

The dataset contains daily passenger counts across multiple transport services, combined into a single total_journeys variable for forecasting. After cleaning and converting the data into a continuous daily time series, several patterns emerged.

### Key Observations

 - Weekly seasonality: Strong weekday peaks and weekend drops dominate the series.

 - Stable long-term trend: No major upward or downward trend across years.

 - Service contributions: Rapid Route, Local Route, and Light Rail make up most of the total journeys.

 - Anomalies present: Occasional unusually low/high days due to holidays or operational changes.

 - Clean structure: No missing values after resampling and filling; data suitable for Prophet modeling.

### Suggested visuals:

 - Daily line plot of total_journeys

 - Weekly seasonality plot

 - Prophet trend/seasonality components

 - Histogram or boxplot of journey distribution

## 6. Final Notes

- Prophet provides a clear, interpretable, and effective forecasting method for datasets with strong recurring seasonal patterns.
- SARIMAX was explored but did not match Prophet’s performance for this specific use case.