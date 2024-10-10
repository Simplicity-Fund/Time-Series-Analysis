# Autocorrelation & Lag

## Lag
Lag represents the shift or time difference between observations in a time series. A lag of 1 means you’re comparing an observation at time t with the observation t-1, a lag of 2 means compering with t-2, and so on.

Lags are crucial because they help capture time-dependent structures, trends, or repeating patterns within the data.

## Autocorrelation
Autocorrelation (also called "serial correlation") measures the correlation between observations of a time series at different time lags. In simpler terms, it quantifies how related the data points at time t are with data points at earlier times t-k (where k is the lag).

- **Positive Autocorrelation**: When a high value is followed by another high value (or a low value followed by another low value).
- **Negative Autocorrelation**: When a high value is followed by a low value, and vice versa.

## Why they are Important

### Understanding Dependencies Over Time
Autocorrelation helps to uncover **time-dependent relationships** in the data. For example:

- **Stock prices**: Prices are often autocorrelated as today's price can be highly related to yesterday's.
- **Sales data**: Seasonal effects or promotional impacts can create recurring patterns, leading to high autocorrelations at specific lags (e.g., weekly or yearly).

Detecting significant autocorrelations at various lags helps to determine the **predictability** of the series and which time intervals (lags) are important for modeling.

### Feature Engineering
In many machine learning models (like regression or neural networks), lagged values (previous data points) are used as input features to predict future values. For example, if the price of an asset depends on its values in the previous 3 days, including lagged versions of the time series as features will enhance model accuracy.

### Stationarity Testing
A stationary time series exhibits constant statistical properties (mean, variance) over time. By analyzing autocorrelation, you can detect trends and seasonality, which are signs of non-stationarity. This helps you decide whether transformations, such as differencing or detrending, are needed to make the series stationary.

## Calculating Autocorrelation

### Autocorrelation Function (ACF) Plot

The Autocorrelation Function (ACF) plot is used to visualize how values at different lags are correlated with the present value. The plot shows the autocorrelation values for a range of lags. Each bar in the plot corresponds to a specific lag, and the height of the bar represents the strength and direction of the correlation at that lag.

**Plot Axis:**
* Lag (x-axis): Represents the number of periods back (lags) you are comparing the series to.
* Autocorrelation (y-axis): Represents the correlation coefficient between the time series and its lagged version. This value ranges from -1 to 1:
    * +1 indicates a perfect positive correlation (the values move together).
    * -1 indicates a perfect negative correlation (the values move in opposite directions).
    * 0 indicates no correlation (the values are independent of each other).

**Characteristics:**
* Spikes in the ACF plot indicate how much a time series is related to its past values.
* A gradual decline in autocorrelation values (bars) as the lag increases typically indicates the presence of a trend in the time series.
    * If autocorrelation slowly decreases over time (lags), this suggests that the time series has a long memory and that past values are influencing future values over a longer time period.
    * A slow decay also suggests that the time series is non-stationary, meaning its statistical properties (like mean and variance) change over time.
* If the ACF plot shows regular spikes at fixed intervals (e.g., every 7 or 12 lags), this indicates seasonality in the data. For example:
    * If you have daily sales data and you see spikes at lags 7, 14, 21, etc., this likely indicates weekly seasonality.
    * If you have monthly temperature data and you see spikes at lag 12, this suggests yearly seasonality (12 months in a year).

**Confidence Intervals in the ACF Plot:**

In an ACF plot, confidence intervals (typically shown as blue or shaded areas) are critical for determining whether the autocorrelation at a given lag is statistically significant.
* Bars outside the confidence intervals: If the bar extends beyond the confidence intervals (typically 95% confidence), it suggests that the autocorrelation at that lag is statistically significant and unlikely to occur by random chance.
* Bars inside the confidence intervals: Bars that fall within the confidence intervals suggest that the autocorrelation is statistically insignificant and could be due to random noise in the data

### Partial Autocorrelation Function (PACF) Plot

The Partial Autocorrelation Function (PACF) plot shows the correlation between a time series and its lags after removing the influence of intermediate lags. This helps to isolate the direct correlation between a value and a specific lag.

While the ACF measures the total correlation between a time series and its lagged values, the PACF isolates the direct correlation by removing the influence of intermediate lags.

By showing only the direct relationships, the PACF plot is especially useful when building autoregressive models, as it helps identify the specific lag order for an AR process.

### Difference Between ACF and PACF

* ACF: Measures the overall correlation between Y(t) and Y(t−k) (including the effects of all intermediate lags).
* PACF: Measures the direct  correlation between Y(t) and Y(t−k), removing the effects of the lags in between (lags 1 through k-1).

If the PACF plot shows a sharp cutoff after a certain lag (e.g., after lag 1 or 2), it suggests the series can be modeled well using an AR model with that lag order. For example:
* A sharp cutoff after lag 1 indicates that an AR(1) model is appropriate.
* A sharp cutoff after lag 2 suggests an AR(2) model.

If the PACF shows a gradual decline (decay) as the lag increases, this indicates that there is no clear cutoff, meaning the series may be more complex and might require higher-order autoregressive or more sophisticated models.

* The ACF plot is useful for detecting overall patterns, trends, and seasonality.
* The PACF is crucial for identifying the appropriate lag order for autoregressive models (AR models).

## Lag Plot
A lag plot visualizes the relationship between the values of the series at time t and time t-k (for different lag values k). This plot helps you see patterns and relationships between current and past values of the series.

* A linear pattern in the lag plot suggests positive autocorrelation (i.e., successive values are related).
* A random scatter indicates little to no autocorrelation at the specified lag.
