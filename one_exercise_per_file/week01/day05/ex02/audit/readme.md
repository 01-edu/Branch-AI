Preliminary:

- As usual the first steps are:

  - Check missing values and data types
  - Convert string dates to datetime
  - Set dates as index
  - Use `info` or `describe` to have a first look at the data

The exercise is not validated if these steps have not been done.

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

- Find how to affect the aggregation on the last **business** day of each month. This is already implemented in Pandas and the keyword that should be used either in `resample` parameter or in `Grouper` is `BM`.
- Choose the right aggregation function for each variable. The prices (Open, Close and Adjusted Close) should be aggregated by taking the `mean`. Low should be aggregated by taking the `minimum` because it represents the lower price of the day, so the lowest price on the month is the lowest price of the lowest prices on the day. The same logic applied to High, leads to use the `maximum` to aggregate the High. Volume should be aggregated using the `sum` because the monthly volume is equal to the sum of daily volume over the month.

    There are **482 months**.

3. The solution is accepted if it doesn't involve a for loop and the output is:

    ```console
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