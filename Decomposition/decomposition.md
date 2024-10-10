# Decomposition

## Components of a Time Series
A time series typically consists of four components:

### Trend (T):
The trend component represents the long-term progression of the series. It captures the overall direction in which the data is moving over time, smoothing out short-term fluctuations.
    
Example: The general increase in the global temperature over decades.
    
Characteristics:

* **Direction**: The trend can be upward, downward, or flat (horizontal).
* **Duration:** Trends can be long-term (spanning years) or short-term (spanning months).
* **Nature:** The trend can be linear or nonlinear. For example, a stock price might increase steadily over a few years (linear) or exhibit exponential growth (nonlinear).

### Seasonality (S):
The seasonal component captures the systematic and predictable variations that occur at specific intervals (such as days, weeks, months, or quarters). These patterns repeat over a fixed period.
Identifying seasonal patterns can help businesses plan for inventory, staffing, and marketing strategies.

Example: Retail sales typically increase in December due to the holiday season.

Characteristics:

- **Regularity**: Seasonality can occur daily, weekly, monthly, etc. For example, retail sales might spike during the holiday season every year.
- **Magnitude**: The seasonal effect can vary in strength; for instance, sales may increase significantly during one holiday season but only slightly during another.

### Noise (Residuals) (R):
The residual component (or error term) represents the random noise in the data. It is what remains after removing the trend and seasonal components from the original time series.

Analyzing residuals helps in evaluating the effectiveness of the decomposition. If residuals show patterns or trends, it may indicate that the model is not adequately capturing the underlying structure of the data. The residuals should ideally be normally distributed and homoscedastic (constant variance) for many statistical models. Evaluating the residuals helps check these assumptions.

In a stock price model, if the residuals show significant clustering or trends over time, it might indicate that important variables or effects are missing from the model. This could prompt further investigation or the inclusion of additional variables.

Example: Unexpected short-term changes in stock prices due to external shocks (e.g., news or events).

Characteristics:

- **Randomness**: Residuals are often assumed to be random and uncorrelated.
- **Unexplained Variability**: They can include sudden market changes, unexpected events, or random fluctuations not accounted for by the trend or seasonality.

### Cyclic Patterns (C):
Cyclic patterns are long-term movements or trends in the data that occur over several years. Unlike seasonal patterns, which repeat at regular intervals, cyclic patterns are influenced by broader economic, political, or social factors.

Recognizing cyclic patterns can help in making long-term forecasts and strategic business decisions. For example, companies can adjust their investment strategies based on expected economic cycles.

Analyzing economic indicators can provide insights into the current phase of the economic cycle (expansion, peak, contraction, trough), allowing businesses and investors to make informed decisions.

Examples:
- **Economic Cycles**: Economic expansion and recession cycles are classic examples of cyclic patterns. For instance, a period of economic growth may last several years, followed by a recession.
- **Business Cycles**: Industries may experience cycles related to the business environment, such as the housing market, which can go through boom and bust cycles over several years.
- **Stock Market Cycles**: The stock market can also show cyclic behavior, where periods of significant gains are followed by downturns, influenced by various factors such as interest rates, economic indicators, and market sentiment.

Characteristics:

- **Duration**: Cycles can last from several years to decades. The length of the cycle is not fixed and can vary significantly.
- **Irregularity**: Unlike seasonal patterns, which are predictable, cyclic patterns can be irregular and less predictable, making them more challenging to identify.
- **Magnitude**: The size of cyclic movements can vary, and the amplitude of fluctuations may change over the duration of the cycle.


## What's Decomposition

Decomposition refers to the process of breaking down a complex data set or time series into simpler, interpretable components. It is particularly useful for understanding the underlying structure of time series data, helping to identify trends, seasonality, and irregular fluctuations.

## Importance of Decomposition

### Understand the Structure of the Data

Time series data often contains complex patterns, such as long-term trends, seasonal variations, and noise. Decomposition allows you to break the series into components that are easier to interpret individually.

By conducting decomposition, you separate these components and can analyze each of them in isolation. This is especially important because different models may be more suitable for different components (e.g., trend models for trends, seasonal models for seasonal data).
Thus decomposition help you predict and analyse each of the components and by putting them together you can predict and analyze the original time series data.

After decomposition, you can:
- Apply different forecasting methods to different components (e.g., trend forecasting for the trend, seasonal forecasting for the seasonal part).
- Use simpler models on the residuals because most systematic behavior has been removed.
- Better handle anomalies by isolating random noise from systematic variations.

### Reveal Hidden Patterns

Sometimes, raw time series data can obscure important insights because the patterns are complex and intertwined. Decomposition helps uncover these hidden patterns that might not be immediately obvious.

Examples:

- In **economic data**, you may not notice cyclical patterns over many years if seasonal variations dominate the short-term view. Decomposition helps you distinguish between short-term and long-term cycles.
- **Sales data** might show a steady upward trend when plotted overall, but decomposition could reveal an **unexpected seasonal drop** in certain months (e.g., lower sales in February), helping you better plan inventory or marketing campaigns.

### Detect Anomalies or Outliers

In time series, unusual spikes or drops in the data can distort your analysis. By decomposing the series, you can separate these irregularities (captured in the residual/noise component) from systematic patterns, making it easier to detect genuine anomalies.

If the residual component is large or irregular, this could indicate outliers or abnormal behavior.

Examples:

- If your **residual** component shows large spikes that can’t be explained by the trend or seasonality, these might represent real-world anomalies (e.g., one-time events like natural disasters, promotions, or system failures).
- In **sensor data**, decomposition can help you filter out expected patterns (like daily temperature fluctuations) and focus on unusual events (like equipment malfunctions).

### Handle Non-Stationary Data

Many forecasting methods (like ARIMA) assume that the time series is stationary. However, most real-world time series are non-stationary due to trends, seasonality, or changing variance. Decomposition helps to isolate non-stationary components (like trends and seasonality) so you can focus on analyzing the stationary part of the data (e.g., the residual).

Examples:

- A **sales dataset** may show non-stationarity due to a strong upward trend (growth in customers) and seasonality (higher sales during certain months). Decomposing the series allows you to handle these non-stationary components separately.

## Decomposition Methods

There are several methods for decomposing time series, each suited for different types of data and decomposition tasks. Let’s go over the two main approaches: **Classical Decomposition** and **STL Decomposition**.

### Classical Decomposition

Classical decomposition assumes the series has a deterministic structure (i.e., fixed, non-varying seasonality and trend). The steps in this method are as follows:

- **Step 1: Estimating Trend (T)**:
    - Apply a **smoothing technique**, such as a moving average, to the series to estimate the trend component.
    - **Centered Moving Average** (CMA) is often used, especially for seasonal data. It involves averaging the series over a sliding window to smooth out short-term fluctuations.
- **Step 2: Estimating Seasonality (S)**:
    - After detrending the series (i.e., subtracting the trend from the original series), average the detrended values for each season (e.g., month or quarter) over multiple cycles to estimate the seasonal component.
    - The seasonal indices repeat after each cycle (e.g., every year).
- **Step 3: Estimating Residuals (R)**:
    - After estimating the trend and seasonality, subtract these from the original series to obtain the residual (or noise) component: R(t) = Y(t) - T(t) - S(t)

### STL Decomposition (Seasonal-Trend Decomposition using LOESS)

**STL decomposition** is a more robust and flexible method compared to classical decomposition, as it handles time-varying seasonality and trends. It uses **LOESS (Locally Estimated Scatterplot Smoothing)**, a non-parametric method, to smooth the data and estimate components.

- **Advantages of STL**:
    - Handles both additive and multiplicative models.
    - Allows for seasonality to change over time (i.e., dynamic seasonality).
    - Provides control over how much smoothing is applied to the trend and seasonal components.

**Steps in STL Decomposition**:

1. **Detrending**: Remove the trend by applying LOESS smoothing to estimate it.
2. **Seasonal Decomposition**: Estimate the seasonal component by smoothing the detrended series (often using LOESS).
3. **Residual**: Subtract the estimated trend and seasonality from the original series to isolate the residual.

STL works well in many situations because it adapts to local fluctuations in both the trend and seasonal components.

## Visualizing Decomposition

Once the decomposition is done, we usually visualize the different components to understand the underlying patterns.
* If the trend is non-linear (e.g., exponential growth), this could indicate that the time series is non-stationary, and you might need to apply transformations (e.g., logarithm) or differencing to make it stationary.

* If the seasonal component is strong, it might suggest that predictions based on this data need to account for these regular fluctuations.

* Ideally, the residual component should resemble white noise (i.e., random fluctuations with no pattern). If patterns remain in the residual, it suggests the decomposition or model is incomplete.
