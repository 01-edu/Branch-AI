# Exercise 6 Unstack

The goal of this exercise is to learn to unstack a MultiIndex
Let's assume we trained a machine learning model that predicts a daily score on the companies (tickers) below. It may be very useful to unstack the MultiIndex: plot the time series, vectorize the backtest, ...

```python
business_dates = pd.bdate_range('2021-01-01', '2021-12-31')

#generate tickers
tickers = ['AAPL', 'FB', 'GE', 'AMZN', 'DAI']

#create indexs
index = pd.MultiIndex.from_product([business_dates, tickers], names=['Date', 'Ticker'])

# create DFs
market_data = pd.DataFrame(index=index,
                        data=np.random.randn(len(index), 1),
                        columns=['Prediction'])

```

1. Unstack the DataFrame.

The first 3 rows of the DataFrame should like this:

| Date                |   ('Prediction', 'AAPL') |   ('Prediction', 'AMZN') |   ('Prediction', 'DAI') |   ('Prediction', 'FB') |   ('Prediction', 'GE') |
|:--------------------|-------------------------:|-------------------------:|------------------------:|-----------------------:|-----------------------:|
| 2021-01-01 00:00:00 |                 0.382312 |                -0.072392 |               -0.551167 |             -0.0585555 |                1.05955 |
| 2021-01-04 00:00:00 |                -0.560953 |                 0.503199 |               -0.79517  |             -3.23136   |                1.50271 |
| 2021-01-05 00:00:00 |                 0.211489 |                 1.84867  |                0.287906 |             -1.81119   |                1.20321 |

2. Plot the 5 times series in the same plot using Pandas built-in visualization functions with a title.