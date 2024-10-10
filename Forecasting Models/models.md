# Time Series Forecasting Models

## Autoregressive (AR) Model
The AutoRegressive (AR) model assumes that the future value of a time series depends on its past values. The "order" of the AR model indicates how many past values (lags) are used to predict the current value.

Equation:

$$
Y_t = c + φ_1Y_{t-1} + φ_2Y_{t-2} + \dots + φ_pY_{t-p} + ε_t
$$

- $Y_t$ : current value at time t
- c : constant term
- $φ_t$ : coefficients (weights) for past values (lags)
- $ε_t$ : error term (white noise)
- p : the order of the AR model (number of lagged terms)

### Steps to Build an AR Model

- **Step 1**: Check for stationarity (using ADF test) because AR models work on stationary data.
- **Step 2**: Choose the lag order (using PACF plot).
- **Step 3**: Estimate the model and evaluate residuals.

## Moving Average (MA) Model

The **Moving Average (MA)** model predicts future values based on past **errors** (residuals). It models the relationship between the current value and past prediction errors.
Equation:

$$
Y_t = c + θ_1ε_{t-1} + θ_2ε_{t-2} + \dots + θ_pε_{t-q} + ε_t
$$

- $θ_t$ : coefficients for the error terms
- $ε_t$ : error term at time t (random shock)
- q : the order of the MA model (number of lagged residuals)

### Steps to Build an MA Model:

- **Step 1**: Check for stationarity.
- **Step 2**: Choose the lag order using the **ACF plot** (ACF helps for MA).
- **Step 3**: Fit and evaluate the model.

## ARMA Model (AutoRegressive Moving Average)

The **ARMA** model combines both **AR** and **MA** components, meaning it accounts for both past values and past residuals.
Equation:

$$
Y_t = c + \sum_{i=1}^{p}φ_iY_t + \sum_{j=1}^{q}θ_iε_t + e_t
$$

## ARIMA (AutoRegressive Integrated Moving Average)

The **ARIMA** model generalizes ARMA by adding **differencing** to handle non-stationary data. It’s a powerful tool for forecasting.
ARIMA is represented as **ARIMA(p, d, q)**:

- **p**: Number of AR terms (lagged values)
- **d**: Differencing order to make the series stationary
- **q**: Number of MA terms (lagged errors)

The differencing step makes the time series stationary by removing trends. This is especially useful for stock prices or time series with trends.

## Seasonal ARIMA (SARIMA)

For time series with clear **seasonality**, ARIMA needs to be extended to account for seasonal patterns. This is where **SARIMA** comes in, represented as **SARIMA(p, d, q) (P, D, Q, s)**:

- **p, d, q**: Regular ARIMA terms (non-seasonal part)
- **P, D, Q**: Seasonal terms for AR, differencing, and MA
- **s**: Seasonal period (e.g., 12 for monthly data with yearly seasonality)

## Evaluating Forecasting Models

Once you have fitted your models, you can evaluate their performance using a variety of techniques and metrics to understand how well the model forecasts. Here's a comprehensive approach to evaluating the forecasting models:

### **In-sample Evaluation**:

In-sample evaluation assesses the model's performance on the training data (i.e., the data used to fit the model). While this can give you some insight into how well the model captures patterns, it's generally better to focus on out-of-sample evaluation to avoid overfitting.

**Metrics for In-sample Evaluation:**

- **Log-likelihood**: This is a likelihood function indicating how likely it is to observe the training data under the given model.
- **AIC (Akaike Information Criterion)**: A metric that balances model fit with model complexity. Lower AIC values indicate better models.
- **BIC (Bayesian Information Criterion)**: Similar to AIC but penalizes complexity more heavily.

### **Out-of-sample Evaluation (on Test Data)**:

This is the most critical evaluation step. It measures how well the model forecasts future data (or unseen data).

**Steps for Out-of-sample Evaluation:**

1. **Generate Forecasts**: Use the fitted model to forecast values beyond the training set.
2. **Compare Forecasts to Actual Values**: Compare the predicted values with the actual values from the test set.

**Metrics for Forecast Evaluation:**

- **Mean Absolute Error (MAE)**: Average of the absolute errors between actual and predicted values.
- **Mean Squared Error (MSE)**: Average of the squared errors between actual and predicted values.
- **Root Mean Squared Error (RMSE)**: Square root of MSE, which penalizes larger errors more heavily.
- **Mean Absolute Percentage Error (MAPE)**: Average percentage difference between predicted and actual values.

### **Residual Analysis**:

Analyzing the residuals (the difference between actual and predicted values) is crucial to check if the model has captured the patterns in the data adequately.

- **Plot the Residuals**: Residuals should ideally behave like white noise (uncorrelated and normally distributed with a mean of zero). You can plot them using:
- **Check for Autocorrelation**: You can check if the residuals are autocorrelated by plotting the **ACF (Autocorrelation Function)**.
    
    If the residuals are autocorrelated, it may indicate that the model has not fully captured the time-dependent structure of the data.
    
- **Q-Q Plot**: A quantile-quantile plot helps assess if the residuals are normally distributed.