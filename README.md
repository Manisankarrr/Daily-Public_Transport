Time Series Forecasting of Daily Public Transport Journeys
1. Dataset Overview

This project uses a daily public transport dataset containing passenger counts across service types such as Local Route, Light Rail, Rapid Route, School, and others.
Data was cleaned, converted into a continuous daily time series, and combined into a single target variable: total_journeys.
The dataset spans multiple years and shows strong weekly seasonality.

2. Forecasting Model Used
Prophet Model

The final forecasting model used is Prophet, chosen because it:

Automatically models weekly seasonality

Handles trend + seasonal patterns cleanly

Produces interpretable components and stable predictions

Why SARIMAX Did Not Fit Well

SARIMAX was tested earlier but underperformed due to:

Its difficulty capturing sharp weekday–weekend shifts

Limited flexibility in modeling non-linear seasonal patterns

Higher forecast error compared to Prophet

Prophet outperformed SARIMAX in stability and overall accuracy.

3. Model Performance & Evaluation
Evaluation Metrics Used

We evaluated the models using:

MAE (Mean Absolute Error)

RMSE (Root Mean Squared Error)

Baseline Result (before cleaning)
Baseline MAE: 22749.25

SARIMAX Result
SARIMAX MAE: 14703.75

Prophet Result
Prophet MAE: 14273.84
Prophet RMSE: 22307.92

4. Key Insights
Insight 1: Prophet Delivered the Most Stable Performance

Prophet achieved the lowest MAE among tested models.
Suggested screenshot: Prophet forecast plot (yhat vs actual).

Insight 2: SARIMAX Struggled With Weekly Seasonality

Large weekend drops were not captured well, leading to higher error.
Suggested screenshot: SARIMAX forecast vs actual plot.

Insight 3: Initial Baseline Was High Due to Unclean Data

The early baseline MAE (22k+) highlighted missing dates and irregularities.
Suggested screenshot: Before/after cleaning time series plot.

Insight 4: Weekly Seasonality Is the Dominant Pattern

Most variation comes from weekday peaks and weekend dips, not long-term trend.
Suggested screenshot: Prophet weekly seasonality component plot.

Insight 5: Prophet Offers Clear Decomposition for Interpretation

Trend, weekly pattern, and residuals are easy to visualize and communicate.
Suggested screenshot: Prophet components plot (trend + weekly).

5. Final Notes

Prophet provides a clear, interpretable, and effective forecasting method for datasets with strong recurring seasonal patterns.
SARIMAX was explored but did not match Prophet’s performance for this specific use case.