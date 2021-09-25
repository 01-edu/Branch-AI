# Exercise 3 Multi asset returns

The goal of this exercise is to learn to compute daily returns on a DataFrame that contains many assets (multi-assets).

```python
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

