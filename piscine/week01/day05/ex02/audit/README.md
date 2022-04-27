##### The exercice is validated is all questions of the exercice are validated

###### Have the missing values and data types been checked ? 
###### Have the string dates been converted to datetime type ? 
###### Have the dates been set as index ? 
###### Have `info` or/and `describe` been used to have a first look at the data ?


##### The question 1 is validated if the right columns are inserted in `Candlestick` `Plotly` object. The Candlestick is based on Open, High, Low and Close columns. The index is Date (datetime). 

##### This question 2 is validated if the output of `print(transformed_df.head().to_markdown())` is as below and if there are **482 months**.

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


##### The question 3 is validated if it doesn't involve a for loop and the output is as below. The first way to do it is to compute the return without for loop is to use `pct_change`. And the second way to do it is to implement the formula given in the exercise in a vectorized way. To get the value at `t-1` the data has to be shifted with `shift`.

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
