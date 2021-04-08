# D04  Piscine AI - Data Science 


Author: 

# Table of Contents:
Historical part: 

Data wrangling, unify source of data ... 
# Introduction



... 
## Ressources 
Pandas website
- https://jakevdp.github.io/PythonDataScienceHandbook/

https://pandas.pydata.org/Pandas_Cheat_Sheet.pdf


https://www.learndatasci.com/tutorials/python-pandas-tutorial-complete-introduction-for-beginners/

https://towardsdatascience.com/different-ways-to-iterate-over-rows-in-a-pandas-dataframe-performance-comparison-dc0d5dcef8fe



# Exercise 1 Concatenate

The goal of this exercise is to learn to concatenate DataFrames. The logic is the same for the Series.

Here are the two DataFrames to concatenate:


```
df1 = pd.DataFrame([['a', 1], ['b', 2]],
                   columns=['letter', 'number'])
df2 = pd.DataFrame([['c', 1], ['d', 2]],
                   columns=['letter', 'number'])

```

1. Concatenate this two DataFrames on index axis and reset the index. The index of the outputted should be `RangeIndex(start=0, stop=4, step=1)`. **Do not change the index manually**.


## Correction

1. This question is validated if the outputted DataFrame is:

    |    | letter   |   number |
    |---:|:---------|---------:|
    |  0 | a        |        1 |
    |  1 | b        |        2 |
    |  2 | c        |        1 |
    |  3 | d        |        2 |


# Exercise 2 Merge

The goal of this exercise is to learn to merge DataFrames
The logic of merging DataFrames in Pandas is quite similar as the one used in SQL. 

Here are the two DataFrames to merge:

```
#df1

df1_dict = {
        'id': ['1', '2', '3', '4', '5'],
        'Feature1': ['A', 'C', 'E', 'G', 'I'],
        'Feature2': ['B', 'D', 'F', 'H', 'J']}

df1 = pd.DataFrame(df1_dict, columns = ['id', 'Feature1', 'Feature2'])

#df2
df2_dict = {
        'id': ['1', '2', '6', '7', '8'],
        'Feature1': ['K', 'M', 'O', 'Q', 'S'],
        'Feature2': ['L', 'N', 'P', 'R', 'T']}

df2 = pd.DataFrame(df2_dict, columns = ['id', 'Feature1', 'Feature2'])
```
1. Merge the two DataFrames to get this output:

    |    |   id | Feature1_x   | Feature2_x   | Feature1_y   | Feature2_y   |
    |---:|-----:|:-------------|:-------------|:-------------|:-------------|
    |  0 |    1 | A            | B            | K            | L            |
    |  1 |    2 | C            | D            | M            | N            |

2. Merge the two DataFrames to get this output: 

    |    |   id | Feature1_df1   | Feature2_df1   | Feature1_df2   | Feature2_df2   |
    |---:|-----:|:---------------|:---------------|:---------------|:---------------|
    |  0 |    1 | A              | B              | K              | L              |
    |  1 |    2 | C              | D              | M              | N              |
    |  2 |    3 | E              | F              | nan            | nan            |
    |  3 |    4 | G              | H              | nan            | nan            |
    |  4 |    5 | I              | J              | nan            | nan            |
    |  5 |    6 | nan            | nan            | O              | P              |
    |  6 |    7 | nan            | nan            | Q              | R              |
    |  7 |    8 | nan            | nan            | S              | T              |

## Correction 

1. This question is validated if the output is: 

    |    |   id | Feature1_x   | Feature2_x   | Feature1_y   | Feature2_y   |
    |---:|-----:|:-------------|:-------------|:-------------|:-------------|
    |  0 |    1 | A            | B            | K            | L            |
    |  1 |    2 | C            | D            | M            | N            |

2. This question is validated if the output is: 

    |    |   id | Feature1_df1   | Feature2_df1   | Feature1_df2   | Feature2_df2   |
    |---:|-----:|:---------------|:---------------|:---------------|:---------------|
    |  0 |    1 | A              | B              | K              | L              |
    |  1 |    2 | C              | D              | M              | N              |
    |  2 |    3 | E              | F              | nan            | nan            |
    |  3 |    4 | G              | H              | nan            | nan            |
    |  4 |    5 | I              | J              | nan            | nan            |
    |  5 |    6 | nan            | nan            | O              | P              |
    |  6 |    7 | nan            | nan            | Q              | R              |
    |  7 |    8 | nan            | nan            | S              | T              |

    Note: Check that the suffixes are set using the suffix parameters rather than manually changing the columns' name. 


## Exercise 3 Merge MultiIndex

The goal of this exercise is to learn to merge DataFrames with MultiIndex. 
Use the code below to generate the DataFrames. `market_data` contains fake market data. In finance, the market is available during the trading days (business days). `alternative_data` contains fake alternative data from social media. This data is available every day. But, for some reasons the Data Engineer lost the last 15 days of alternative data. 

1. Using `market_data` as the reference, merge `alternative_data` on `market_data`

    ```
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

https://medium.com/swlh/merging-dataframes-with-pandas-pd-merge-7764c7e2d46d



## Correction 

1. This question is validated if the outputted DataFrame's shape is `(1305, 5)` and if `merged.head()` returns:

|                                                      |       Open |     Close |   Close_Adjusted |     Twitter |    Reddit |
|:-----------------------------------------------------|-----------:|----------:|-----------------:|------------:|----------:|
| (Timestamp('2021-01-01 00:00:00', freq='B'), 'AAPL') |  0.0991792 | -0.31603  |         0.634787 | -0.00159041 |  1.06053  |
| (Timestamp('2021-01-01 00:00:00', freq='B'), 'FB')   | -0.123753  |  1.00269  |         0.713264 |  0.0142127  | -0.487028 |
| (Timestamp('2021-01-01 00:00:00', freq='B'), 'GE')   | -1.37775   | -1.01504  |         1.2858   |  0.109835   |  0.04273  |
| (Timestamp('2021-01-01 00:00:00', freq='B'), 'AMZN') |  1.06324   |  0.841241 |        -0.799481 | -0.805677   |  0.511769 |
| (Timestamp('2021-01-01 00:00:00', freq='B'), 'DAI')  | -0.603453  | -2.06141  |        -0.969064 |  1.49817    |  0.730055 |

One of the answers that returns the correct DataFrame is: 

`market_data.merge(alternative_data, how='left', left_index=True, right_index=True)`

2. This question is validated if the number of missing in the DataFrame is equal to 0 and if `filled_df.sum().sum() == merged_df.sum().sum()` gives: `True`


# Exercise 4 Groupby Apply

The goal of this exercise is to learn to group the data and apply a function on the groups. 
The use case we will work on is computing 

1. Create a function that uses `pandas.DataFrame.clip` and that replace extreme values by a given percentile. The values that are greater than the upper percentile 80% are replaced by the percentile 80%. The values that are smaller than the lower percentile 20% are replaced by the percentile 20%. This process that correct outliers is called **winsorizing**. 
I recommend to use NumPy to compute the percentiles to make sure we used the same defaut parameters. 


    ```
        def winsorize(df, quantiles):
            """
                df: pd.DataFrame
                quantiles: list 
                    ex: [0.05, 0.95]
            """
            #TODO
            return 
    ```
    Here is what the function should output: 

    ```
        df = pd.DataFrame(range(1,11), columns=['sequence'])
        print(winsorize(df, [0.20, 0.80]).to_markdown())

    ```


    |    |   sequence |
    |---:|-----------:|
    |  0 |        2.8 |
    |  1 |        2.8 |
    |  2 |        3   |
    |  3 |        4   |
    |  4 |        5   |
    |  5 |        6   |
    |  6 |        7   |
    |  7 |        8   |
    |  8 |        8.2 |
    |  9 |        8.2 |


2. Now we consider that each value belongs to a group. The goal is to apply the **winsorizing to each group**. In this question we use winsorizing values that are common: `[0.05,0.95]` as percentiles. Here is the new data set: 

    ```
    groups = np.concatenate([np.ones(10), np.ones(10)+1,  np.ones(10)+2, np.ones(10)+3, np.ones(10)+4])
    
    df = pd.DataFrame(data= zip(groups,
                                range(1,51)),
                    columns=["group", "sequence"])
    ```
    The expected output (first rows) is:

    |    |   sequence |
    |---:|-----------:|
    |  0 |       1.45 |
    |  1 |       2    |
    |  2 |       3    |
    |  3 |       4    |
    |  4 |       5    |
    |  5 |       6    |
    |  6 |       7    |
    |  7 |       8    |
    |  8 |       9    |
    |  9 |       9.55 |
    | 10 |      11.45 |


## Correction
The for loop is forbidden in this exercise. The goal is to use `groupby` and `apply`. 

1.  This question is validated if the output is:

    ```
        df = pd.DataFrame(range(1,11), columns=['sequence'])
        print(winsorize(df, [0.20, 0.80]).to_markdown())

    ```


    |    |   sequence |
    |---:|-----------:|
    |  0 |        2.8 |
    |  1 |        2.8 |
    |  2 |        3   |
    |  3 |        4   |
    |  4 |        5   |
    |  5 |        6   |
    |  6 |        7   |
    |  7 |        8   |
    |  8 |        8.2 |
    |  9 |        8.2 |


2. This question is validated if the output is the same as the one returned by: 

    ```
    def winsorize(df_series, quantiles):
    """
        df: pd.DataFrame or pd.Series
        quantiles: list [0.05, 0.95]
    
    """
    min_value = np.quantile(df_series, quantiles[0])
    max_value = np.quantile(df_series, quantiles[1])
    
    return df_series.clip(lower = min_value, upper = max_value)


    df.groupby("group")[['sequence']].apply(winsorize, [0.05,0.95])
    ```
    The ouput can also be a Series instead of a DataFrame.

    The expected output (first rows) is:

    |    |   sequence |
    |---:|-----------:|
    |  0 |       1.45 |
    |  1 |       2    |
    |  2 |       3    |
    |  3 |       4    |
    |  4 |       5    |
    |  5 |       6    |
    |  6 |       7    |
    |  7 |       8    |
    |  8 |       9    |
    |  9 |       9.55 |
    | 10 |      11.45 | 

https://towardsdatascience.com/how-to-use-the-split-apply-combine-strategy-in-pandas-groupby-29e0eb44b62e



# Exercise 5 Groupby Agg

The goal of this exercise is to learn to compute different type of agregations on the groups. This small DataFrame contains products and prices. 

|    |   value | product      |
|---:|--------:|:-------------|
|  0 |   20.45 | table        |
|  1 |   22.89 | chair        |
|  2 |   32.12 | chair        |
|  3 |  111.22 | mobile phone |
|  4 |   33.22 | table        |
|  5 |  100    | mobile phone |
|  6 |   99.99 | table        |

1. Compute the min, max and mean price for each product in one single line of code. The expected output is: 

| product      |   ('value', 'min') |   ('value', 'max') |   ('value', 'mean') |
|:-------------|-------------------:|-------------------:|--------------------:|
| chair        |              22.89 |              32.12 |              27.505 |
| mobile phone |             100    |             111.22 |             105.61  |
| table        |              20.45 |              99.99 |              51.22  |

Note: The columns don't have to be MultiIndex

## Correction

1. The question is validated if the output is: 

| product      |   ('value', 'min') |   ('value', 'max') |   ('value', 'mean') |
|:-------------|-------------------:|-------------------:|--------------------:|
| chair        |              22.89 |              32.12 |              27.505 |
| mobile phone |             100    |             111.22 |             105.61  |
| table        |              20.45 |              99.99 |              51.22  |

Note: The columns don't have to be MultiIndex

My answer is: `df.groupby('product').agg({'value':['min','max','mean']})`

# Exercise 6 Unstack 

The goal of this exercise is to learn to unstack a MultiIndex. 
Let's assume we trained a machine learning model that predicts a daily score on the companies (tickers) below. It may be very useful to unstack the MultiIndex: plot the time series, vectorize the backtest etc ... 

```
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


2. Plot the 5 times series in the same plot using Pandas built-in visualisation functions with a title. 


## Correction 

1. This questions is validated is the output of `unstacked_df.head()` is 

    | Date                |   ('Prediction', 'AAPL') |   ('Prediction', 'AMZN') |   ('Prediction', 'DAI') |   ('Prediction', 'FB') |   ('Prediction', 'GE') |
    |:--------------------|-------------------------:|-------------------------:|------------------------:|-----------------------:|-----------------------:|
    | 2021-01-01 00:00:00 |                 0.382312 |                -0.072392 |               -0.551167 |             -0.0585555 |                1.05955 |
    | 2021-01-04 00:00:00 |                -0.560953 |                 0.503199 |               -0.79517  |             -3.23136   |                1.50271 |
    | 2021-01-05 00:00:00 |                 0.211489 |                 1.84867  |                0.287906 |             -1.81119   |                1.20321 |

2. The question is validated if the answer is: `unstacked.plot(title = 'Stocks 2021')`. The title can be anything else. 


