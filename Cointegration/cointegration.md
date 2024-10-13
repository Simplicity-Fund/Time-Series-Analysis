# Cointegrated Variables
Two or more non-stationary variables are said to be cointegrated if they have a long-term, stable relationship despite being individually non-stationary.

Even if two variables are non-stationary, they can be "linked" in such a way that their combination (a linear combination of the two) is stationary. This means that while the variables themselves may drift over time, they move together in a way that keeps their relationship stable in the long run.

## Mathematical Intuition

Suppose you have two non-stationary time series, $X_t$ and $Y_t$, both of which follow a stochastic trend. Individually, they are non-stationary, but there exists some coefficient $β$  such that:

$$
Z_t = X_t - βY_t
$$

Where $Z_t$ is stationary. If such β exists then the two variables are cointegrated.

## Why is Cointegration Important?

Cointegration provides a way to model relationships between non-stationary time series. It’s especially important in fields like finance and economics, where many variables (e.g., stock prices, exchange rates, interest rates) are non-stationary.

If two series are cointegrated, it means:

- They have a meaningful economic relationship.
- We can use one to predict the other in the long term.
- There’s a mechanism pulling them back together even if they deviate in the short run.

## Examples of Cointegration

### Example 1: Stock Prices of Related Companies

Consider the stock prices of two companies, say **Coca-Cola** and **Pepsi**. Each stock price individually might trend upward due to long-term economic growth (making them non-stationary), but because the companies operate in the same industry and face similar market conditions, their stock prices might be cointegrated. The spread between their stock prices could be stationary, indicating a long-term equilibrium relationship.

### Example 2: Interest Rates

The **short-term and long-term interest rates** on bonds might be non-stationary because of economic policies, inflation, etc. However, they are often cointegrated because they tend to follow each other in the long run due to market arbitrage. If the short-term rate rises significantly above the long-term rate, it will likely correct itself over time.

## How to Test for Cointegration

There are several ways to test if two variables are cointegrated. The two most common methods are the **Engle-Granger Test** and the **Johansen Test**. Before testing for cointegration, you should check if each time series is non-stationary, as cointegration only applies to non-stationary variables.

## Practical Considerations

- **Error Correction Model (ECM)**: If two variables are cointegrated, you can use an Error Correction Model to model short-term deviations from the long-run equilibrium while maintaining the long-term relationship. It allows you to capture both short-term dynamics and long-term trends.
- **Number of Cointegrating Relationships**: The Johansen test, unlike the Engle-Granger test, can also detect multiple cointegrating vectors if more than two variables are involved.