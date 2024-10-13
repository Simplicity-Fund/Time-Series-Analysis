# Multivariate Modeling

Multivariate Time Series Modeling involves the analysis and forecasting of multiple time series that influence each other. Unlike univariate models, which only account for one variable, **multivariate time series models** capture the interactions between multiple variables over time, making them more powerful when there is a clear interdependence between variables.

This type of analysis is particularly useful when dealing with complex systems where the evolution of one variable is influenced by others, like stock prices, economic indicators, or sensor data in industrial applications.

## Key Concepts of Multivariate Time Series

- **Multiple Variables**: In multivariate time series, we deal with multiple variables or features that evolve over time. For example, in finance, you may analyze stock prices, trading volume, interest rates, and inflation data simultaneously.
- **Lag Relationships**: Just like in univariate time series, lagged values of one variable can affect its own future values. In multivariate analysis, lags of one variable can also influence the future values of other variables. These cross-variable lag relationships are essential for understanding the dynamics.
- **Stationarity**: As in univariate time series, it’s important to check for stationarity in multivariate time series as well. If the variables exhibit trends or seasonality, differencing or detrending is necessary.

## Common Models for Multivariate Time Series

### Vector Autoregression (VAR) Model

The **VAR** model is the foundational model for multivariate time series. It extends the univariate AR model to multiple time series by allowing for the interdependencies between them.
In a VAR model, each variable in the system is modeled as a linear function of its own lags and the lags of all other variables.
Formula:

$$
y_{1,t} = c_1 + φ_{11}y_{1,t-1} + φ_{12}y_{2, t-1} + \dots + ε_{1, t}
$$

$$
y_{2,t} = c_2 + φ_{21}y_{2,t-1} + φ_{22}y_{1, t-1} + \dots + ε_{2, t}
$$

where, $y_{1,t}$ and $y_{2, t}$ are the two variables at time t.