# D05  Piscine AI - Data Science 

The goal of this day is to understand practical usage of Pandas. 
Today we will discover some important functionalities of Pandas. they will allow you to manipulate the data (DataFrame and Series) in order to clean, delete, add, merge and leverage more information. 

In Data Science this is crucial, because without cleaned data there's no algorithms learning. 



Author: 

# Table of Contents:
Historical part: 


# Introduction

Not only is the pandas library a central component of the data science toolkit but it is used in conjunction with other libraries in that collection.

Pandas is built on top of the NumPy package, meaning a lot of the structure of NumPy is used or replicated in Pandas. Data in pandas is often used to feed statistical analysis in SciPy, plotting functfunctionsions from Matplotlib, and machine learning algorithms in Scikit-learn.

## Historical

## Rules
... 
## Ressources 
Pandas website
- https://jakevdp.github.io/PythonDataScienceHandbook/

https://pandas.pydata.org/Pandas_Cheat_Sheet.pdf
https://www.learndatasci.com/tutorials/python-pandas-tutorial-complete-introduction-for-beginners/


# Exercise 1

The goal of this exercise is to learn to manipulate time series in Pandas. 

1. Create a `Series` named `integer_series`from 1st January 2010 to 31 December 2020. At each date is associated the number of days since 1st January 2010. It starts with 0.

2. Using Pandas, compute a 7 days moving average. This transformation smooths the time series by removing small fluctuations.   **without for loop**



## Correction

1. This question is validated if the output of is 

    ```
    2010-01-01       0
    2010-01-02       1
    2010-01-03       2
    2010-01-04       3
    2010-01-05       4
                ... 
    2020-12-27    4013
    2020-12-28    4014
    2020-12-29    4015
    2020-12-30    4016
    2020-12-31    4017
    Freq: D, Name: integer_series, Length: 4018, dtype: int64
    ```
    The best solution uses `pd.date_range` to generate the index and `range` to generate the integer series. 

2. This question is validated if the output is: 

    ```
    2010-01-01       NaN
    2010-01-02       NaN
    2010-01-03       NaN
    2010-01-04       NaN
    2010-01-05       NaN
                ...  
    2020-12-27    4010.0
    2020-12-28    4011.0
    2020-12-29    4012.0
    2020-12-30    4013.0
    2020-12-31    4014.0
    Freq: D, Name: integer_series, Length: 4018, dtype: float64
    ```
    If the `NaN` values have been dropped the solution is also accepted. The solution uses `rolling().mean()`. 

# Exercise 2

The goal of this exercise is to learn to use Pandas on Time Series an on Financial data. 

The data we will use is Apple stock. 

1. Using `Plotly` plot a Candlestick 

2. Agregate the data to **last business day of each month**. The agregation should consider the meaning of the variables. How many months are in the considered period ? 

3. When comparing many stocks between them the metric which is frequently used is the return of the price. The price is not a convinient metric as the prices evolve in different ranges. The return at time t is defined as 

    -  (Price(t) - Price(t-1))/ Price(t-1)

    Using the open price compute the **daily return**. Propose two different ways **without for loop**.  


## Correction:
Preliminary: 

- As usual the first steps are:

    - Check missing values and data types
    - Convert string dates to datetime
    - Set dates as index
    - Use `info` or `describe` to have a first look at the data

The exerice is not validated if these steps haven't been done. 
1. The Candlestick is based on Open, High, Low and Close columns. The index is Date (datetime). As long as you inserted the right columns in `Candlestick` `Plotly` object you validate the question.

2. This question is validated if the output of `print(transformed_df.head().to_markdown())` is

| Date                |     Open |    Close |      Volume |     High |      Low |
|:--------------------|---------:|---------:|------------:|---------:|---------:|
| 1980-12-31 00:00:00 | 0.136075 | 0.135903 | 1.34485e+09 | 0.161272 | 0.112723 |
| 1981-01-30 00:00:00 | 0.141768 | 0.141316 | 6.08989e+08 | 0.155134 | 0.126116 |
| 1981-02-27 00:00:00 | 0.118215 | 0.117892 | 3.21619e+08 | 0.128906 | 0.106027 |
| 1981-03-31 00:00:00 | 0.111328 | 0.110871 | 7.00717e+08 | 0.120536 | 0.09654  |
| 1981-04-30 00:00:00 | 0.121811 | 0.121545 | 5.36928e+08 | 0.131138 | 0.108259 |

To get this result there are two ways: `resample` and `groupby`. There are two key steps:

-  Find how to affect the agregation on the last **business** day of each month. This is already implemented in Pandas and the keyword that should be used either in `resample` parameter or in `Grouper` is `BM`. 
- Choose the right agregation function for each variable. The prices (Open, Close and Adjusted Close) should be agregated by taking the `mean`. Low should be agregated by taking the `minimum` because it represents the lower price of the day, so the lowest price on the month is the lowest price of the lowest prices on the day. The same logic applied to High, leads to use the `maximum` to agregate the High. Volume should be agregated using the `sum` because the monthly volume is equal to the sum of daily volume over the month. 

    There are **482 months**. 

3. The solution is accepted if it doesn't involve a for loop and the output is:

    ```
    Date
    1980-12-12         NaN
    1980-12-15   -0.047823
    1980-12-16   -0.073063
    1980-12-17    0.019703
    1980-12-18    0.028992
                    ...   
    2021-01-25    0.049824
    2021-01-26    0.003704
    2021-01-27   -0.001184
    2021-01-28   -0.027261
    2021-01-29   -0.026448
    Name: Open, Length: 10118, dtype: float64
    ```
    - The first way is to compute the return without for loop is to use `pct_change`
    - The second way to compute the return without for loop is to implement the formula given in the exercise in a vectorized way. To get the value at `t-1` you can use `shift`

# Exercise 3 Multi asset returns

The goal of this exercise is to learn to compute daily returns on a DataFrame that contains many assets (multi-assets). 

```
business_dates = pd.bdate_range('2021-01-01', '2021-12-31')

#generate tickers
tickers = ['AAPL', 'FB', 'GE', 'AMZN', 'DAI']

#create indexs
index = pd.MultiIndex.from_product([business_dates, tickers], names=['Date', 'Ticker'])

# create DFs
market_data = pd.DataFrame(index=index,
                        data=np.random.randn(len(index), 1),
                        columns=['Price'])
```
1. **Without using a for loop**, compute the daily returns (return(d) = (price(d)-price(d-1))/price(d-1)) for all the companies and returns a DataFrame as: 

| Date                |   ('Price', 'AAPL') |   ('Price', 'AMZN') |   ('Price', 'DAI') |   ('Price', 'FB') |   ('Price', 'GE') |
|:--------------------|--------------------:|--------------------:|-------------------:|------------------:|------------------:|
| 2021-01-01 00:00:00 |          nan        |         nan         |          nan       |        nan        |         nan       |
| 2021-01-04 00:00:00 |            1.01793  |           0.0512955 |            3.84709 |         -0.503488 |           0.33529 |
| 2021-01-05 00:00:00 |           -0.222884 |          -1.64623   |           -0.71817 |         -5.5036   |          -4.15882 |

Note: The data is generated randomly, the values you may have a different results. But, this shows the expected DataFrame structure. 

`Hint use groupby`

## Correction

1. This question is validated if, without having used a for loop, the outputted DataFrame shape's `(261, 5)` and your output is the same as the one return with this line of code: 

    ```
    market_data.loc[market_data.index.get_level_values('Ticker')=='AAPL'].sort_index().pct_change()

    ```
The DataFrame contains random data. Make sure your output and the one returned by this code is based on the same DataFrame. 


# Exercise 4 Backtest

The goal of this exercise is to learn to perform a backtest in Pandas. A backtest is a tool that allows you to know how a strategy would have performed retrospectively using historical data. In this exercise we will focus on the backtesting tool and not on how to build the best strategy. 

We will backtest a **long only** strategy on Apple Inc. Long only means that we only consider buying the stock. The input signal at date d says if the close price will increase at d+1. We assume that the input signal is available before the market closes. 


1. Drop the rows with missing values and compute the daily futur return on the Apple stock on the adjusted close price. The daily futur return means: **Return(t) = (Price(t+1) - Price(t))/Price(t)**.
There are some events as splits or dividents that artificially change the price of the stock. That is why the close price is adjusted to avoid to have outliers in the price data. 

2. Create a Series that contains a random boolean array with **p=0.5** 

    ```
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
    (money earned this day - money invested this day) 
    Let's take the example of a 20% return for an invested amount of 1$. The PnL is (1,2 - 1) = 0.2. We notice that the PnL when the signal is 1 equals the daily return. The Pnl when the signal is 0 is 0. 
    By convention, we consider that the PnL of d is affected to day d and not d+1, even if the underlying return contains the information of d+1. 

    **The usage of for loop is not allowed**. 

4. Compute the return of the strategy. The return of the strategy is defined as: (Total earned - Total invested) / Total invested

5. Now the input signal is: **always buy**. Compute the daily PnL and the total PnL. Plot the daily PnL of Q5 and of Q3 on the same plot

https://www.investopedia.com/terms/b/backtesting.asp


## Correction
Preliminary: 

- As usual the first steps are:

    - Check missing values and data types
    - Convert string dates to datetime
    - Set dates as index
    - Use `info` or `describe` to have a first look at the data

The exerice is not validated if these steps haven't been done. 

My results can be reproduced using: `np.random.seed = 2712`. Given the versions of NumPy used I do not garanty the reproducibilty of the results - that is why I also explain the steps to get to the solution. 


1. This question is validated if the return is computed as: Return(t) = (Price(t+1) - Price(t))/Price(t) and returns this output. 

    ```
        Date
        1980-12-12   -0.052170
        1980-12-15   -0.073403
        1980-12-16    0.024750
        1980-12-17    0.029000
        1980-12-18    0.061024
                        ...   
        2021-01-25    0.001679
        2021-01-26   -0.007684
        2021-01-27   -0.034985
        2021-01-28   -0.037421
        2021-01-29         NaN
        Name: Daily_futur_returns, Length: 10118, dtype: float64

    ```
    The answer is also accepted if the returns is computed  as in the exercise 2 and then shifted in the futur using `shift`, but I do not recommend this implementation as it adds missing values ! 
    An example of solution is:


    ```
        def compute_futur_return(price):
        return (price.shift(-1) - price)/price

        compute_futur_return(df['Adj Close'])
    ```
    Note that if the index is not ordered in ascending order the futur return computed is wrong.

2. This question is validated if the index of the Series is the same as the index of the DataFrame. The data of the series can be generated using `np.random.randint(0,2,len(df.index)`.

3. This question is validated if the Pnl is computed as: signal * futur_return. Both series should have the same index.

```
    Date
    1980-12-12   -0.052170
    1980-12-15   -0.073403
    1980-12-16    0.024750
    1980-12-17    0.029000
    1980-12-18    0.061024
                    ...   
    2021-01-25    0.001679
    2021-01-26   -0.007684
    2021-01-27   -0.034985
    2021-01-28   -0.037421
    2021-01-29         NaN
    Name: PnL, Length: 10119, dtype: float64
```

4. The question is validated if you computed the return of the strategy as: (Total earned - Total invested) / Total invested. The result should be close to 0. The formula given could be simplified as `(PnLs.sum())/signal.sum()`.
My return is: 0.00043546984088551553 because I invested 5147$ and I earned 5149$.


5. The question is validated if you replaced the previous signal Series with 1s. Similarly as the previous question, we earned 10128$ and we invested 10118$ which leads to a return of 0.00112670194140969 (0.1%).

