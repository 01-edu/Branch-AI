# Exercise 4 Backtest

The goal of this exercise is to learn to perform a backtest in Pandas. A backtest is a tool that allows you to know how a strategy would have performed retrospectively using historical data. In this exercise we will focus on the backtesting tool and not on how to build the best strategy.

We will backtest a **long only** strategy on Apple Inc. Long only means that we only consider buying the stock. The input signal at date d says if the close price will increase at d+1. We assume that the input signal is available before the market closes.

1. Drop the rows with missing values and compute the daily futur return on the Apple stock (`AAPL.csv`) on the adjusted close price. The daily futur return means: **Return(t) = (Price(t+1) - Price(t))/Price(t)**.
There are some events as splits or dividents that artificially change the price of the stock. That is why the close price is adjusted to avoid to have outliers in the price data.

2. Create a Series that contains a random boolean array with **p=0.5**

    ```console
    Here an example of the expected time series
    2010-01-01    1
    2010-01-02    0
    2010-01-03    0
    2010-01-04    1
    2010-01-05    0
    Freq: D, Name: long_only_signal, dtype: int64
    ```

    - The information is this series should be interpreted this way:
        - On the 2010-01-01 I receive `1` before the market closes meaning that, if I trust the signal, the close price of day d+1 will increase. I should buy the stock before the market closes.
        - On the 2010-01-02 I receive `0` before the market closes meaning that,, if I trust the signal, the close price of day d+1 will not increase. I should not buy the stock.

3. Backtest the signal created in Question 2. Here are some assumptions made to backtest this signal:
    - When, at date d, the signal equals 1 we buy 1$ of stock just before the market closes and we sell the stock just before the market closes the next day.
    - When, at date d, the signal equals 0, we do not buy anything.
    - The profit is not reinvested, when invested, the amount is always 1$.
    - Fees are not considered

    **The expected output** is a **Series that gives for each day the return of the strategy. The return of the strategy is the PnL (Profit and Losses) divided by the invested amount**. The PnL for day d is:
    `(money earned this day - money invested this day)`

    Let's take the example of a 20% return for an invested amount of 1$. The PnL is `(1,2 - 1) = 0.2`. We notice that the PnL when the signal is 1 equals the daily return. The Pnl when the signal is 0 is 0.
    By convention, we consider that the PnL of d is affected to day d and not d+1, even if the underlying return contains the information of d+1.

    **The usage of for loop is not allowed**.

4. Compute the return of the strategy. The return of the strategy is defined as: `(Total earned - Total invested) / Total invested`

5. Now the input signal is: **always buy**. Compute the daily PnL and the total PnL. Plot the daily PnL of Q5 and of Q3 on the same plot

- https://www.investopedia.com/terms/b/backtesting.asp
