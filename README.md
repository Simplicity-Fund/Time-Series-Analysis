# Time-Series-Analysis
This repository contains a collection notes, and concepts on various topics related to Time Series Analysis, including decomposition, stationarity, autocorrelation, and more as we continue to explore this fascinating field.

## Introduction
Time Series Analysis is a powerful tool used to analyze temporal data points collected over time. This repository documents key concepts, methods, and techniques used in the field to understand patterns, forecast future data, and extract meaningful insights from time-dependent data.

## Concepts
### Time Series Decomposition
Decomposition of time series is the process of breaking down a series into its individual components:
- **Trend**: Represents the long-term movement in the data over time.
- **Seasonal**: Shows repeating short-term cycles (e.g., weekly, monthly).
- **Residual (Noise)**: Represents the remaining variation that cannot be attributed to the trend or seasonality.

### Stationarity
Stationarity is a critical assumption in many time series models. A stationary time series has constant mean, variance, and covariance over time.

Common tests to check for stationarity include:
- **Augmented Dickey-Fuller (ADF) Test**: A hypothesis test to check if a unit root is present in the series.
- **KPSS Test**: Tests for the null hypothesis of stationarity against the alternative of a unit root.

### Autocorrelation
Autocorrelation measures the relationship between a time series and its lagged values.

To calculate autocorrelation we have:
* **Autocorrelation Function (ACF)**: measures the correlation between a time series and lagged versions of itself. It helps to identify the presence of any repeating patterns or seasonality.
* **Partial Autocorrelation Function (PACF)**: measures the correlation between a time series and its lagged values after removing the influence of intermediate lags.

## Conclusion
This repository serves as a living document where we will continue to add new concepts and techniques related to Time Series Analysis. Stay tuned for more updates on topics like forecasting, ARIMA models, seasonal adjustment, and much more.
