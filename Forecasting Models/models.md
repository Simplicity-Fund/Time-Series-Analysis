# Time Series Forecasting Models

## Autoregressive (AR) Model
The AutoRegressive (AR) model assumes that the future value of a time series depends on its past values. The "order" of the AR model indicates how many past values (lags) are used to predict the current value.

Equation:

$$
Y_t = c + φ_1Y_{t-1} + φ_2Y_{t-2} + \dots + φ_pY_{t-p} + ε_t
&&

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
