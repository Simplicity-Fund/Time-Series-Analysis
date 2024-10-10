# Stationarity

Stationarity is a fundamental concept in time series analysis, and determining whether a time series is stationary or non-stationary is crucial for many statistical methods and models. Let’s break down why stationarity is important and how to detect it in your time series data.

A time series is said to be stationary if its statistical properties, such as mean, variance, and autocorrelation, are constant over time. In contrast, a non-stationary time series shows changing statistical properties over time.

- **Strict Stationarity**: The joint distribution of any subset of the time series is the same, regardless of the time at which the subset is taken. This is a stronger definition.
- **Weak Stationarity (Covariance Stationarity)**: The mean, variance, and covariance are constant over time. This is the more commonly used, practical definition in most time series analyses.

Stationarity is crucial because many time series forecasting methods and models, such as ARIMA (AutoRegressive Integrated Moving Average) or Exponential Smoothing, assume that the underlying time series is stationary. If the time series is non-stationary, the model's assumptions might not hold, leading to unreliable results.

## Properties of a Stationary Series

1. **Constant Mean**: The series hovers around a fixed mean value over time.
2. **Constant Variance**: The variability or spread of the time series remains the same.
3. **Constant Covariance**: The relationship between values at different time points depends only on the time difference between them (not the actual time itself).

## Checking Stationarity

### Visual Inspection
A simple plot can give you a sense of whether the series has a constant mean and variance. If the series shows clear upward or downward trends or significant changes in variance over time, it is likely non-stationary.

You can, also, calculate the rolling mean and rolling standard deviation over a window of time and plot them to see if they remain constant over time. If the rolling statistics change, the time series is non-stationary.

### Statistical Tests for Stationarity

The **ADF Test** is a widely used statistical test to determine whether a time series is stationary. It tests the null hypothesis that the time series is non-stationary.
* If the p-value is less than 0.05, the time series is stationary (reject the null hypothesis).
* If the p-value is greater than 0.05, the time series is non-stationary (fail to reject the null hypothesis).

The **KPSS Test** is another test that checks for stationarity but with the opposite null hypothesis: it tests whether a time series is stationary. A small p-value here suggests non-stationarity.
* If the p-value is small, the time series is non-stationary.
* If the p-value is large, the time series is stationary.

## Making a Time Series Stationary

### Differencing
This technique involves subtracting the current observation from the previous one to remove trends or seasonality.

### Log Transformation
Log transformations can stabilize the variance and make the series more stationary.

### Detrending
Detrending is the process of removing the underlying trend from a time series to make it stationary. Trends are long-term increases or decreases in data values that are not necessarily indicative of repeating cycles or seasonal variations. Detrending is essential when analyzing time series data because many statistical and machine learning models assume that the data is stationary.

Before applying detrending, it’s important to understand the nature of the trend in your data:

1. Linear Trend: A straight upward or downward movement over time. It can be captured by a linear function.
2. Non-Linear Trend: A curved, exponential, or polynomial trend. This type of trend requires more sophisticated techniques to remove.
3. Piecewise Trend: A trend that might change direction at different points in time, requiring a segmented approach.
