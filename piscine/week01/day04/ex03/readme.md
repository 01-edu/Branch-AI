# Exercise 3 Merge MultiIndex

The goal of this exercise is to learn to merge DataFrames with MultiIndex.
Use the code below to generate the DataFrames. `market_data` contains fake market data. In finance, the market is available during the trading days (business days). `alternative_data` contains fake alternative data from social media. This data is available every day. But, for some reasons the Data Engineer lost the last 15 days of alternative data.

1. Using `market_data` as the reference, merge `alternative_data` on `market_data`

    ```python
    #generate days
    all_dates = pd.date_range('2021-01-01', '2021-12-15')
    business_dates = pd.bdate_range('2021-01-01', '2021-12-31')

    #generate tickers
    tickers = ['AAPL', 'FB', 'GE', 'AMZN', 'DAI']

    #create indexs
    index_alt = pd.MultiIndex.from_product([all_dates, tickers], names=['Date', 'Ticker'])
    index = pd.MultiIndex.from_product([business_dates, tickers], names=['Date', 'Ticker'])

    # create DFs
    market_data = pd.DataFrame(index=index,
                            data=np.random.randn(len(index), 3),
                            columns=['Open','Close','Close_Adjusted'])

    alternative_data = pd.DataFrame(index=index_alt,
                                    data=np.random.randn(len(index_alt), 2),
                                    columns=['Twitter','Reddit'])
    ```

`reset_index` is not allowed for this question

2. Fill missing values with 0

- https://medium.com/swlh/merging-dataframes-with-pandas-pd-merge-7764c7e2d46d
