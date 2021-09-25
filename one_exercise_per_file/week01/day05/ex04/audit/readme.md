Preliminary:

- As usual the first steps are:

  - Check missing values and data types
  - Convert string dates to datetime
  - Set dates as index
  - Use `info` or `describe` to have a first look at the data

The exercise is not validated if these steps haven't been done.

My results can be reproduced using: `np.random.seed = 2712`. Given the versions of NumPy used I do not guaranty the reproducibility of the results - that is why I also explain the steps to get to the solution.

1. This question is validated if the return is computed as: Return(t) = (Price(t+1) - Price(t))/Price(t) and returns this output.

    ```console
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

    ```python
        def compute_futur_return(price):
        return (price.shift(-1) - price)/price

        compute_futur_return(df['Adj Close'])
    ```

    Note that if the index is not ordered in ascending order the futur return computed is wrong.

2. This question is validated if the index of the Series is the same as the index of the DataFrame. The data of the series can be generated using `np.random.randint(0,2,len(df.index)`.

3. This question is validated if the Pnl is computed as: signal * futur_return. Both series should have the same index.

```console
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

4. The question is validated if you computed the return of the strategy as: `(Total earned - Total invested) / Total` invested. The result should be close to 0. The formula given could be simplified as `(PnLs.sum())/signal.sum()`.

My return is: 0.00043546984088551553 because I invested 5147$ and I earned 5149$.

5. The question is validated if you replaced the previous signal Series with 1s. Similarly as the previous question, we earned 10128$ and we invested 10118$ which leads to a return of 0.00112670194140969 (0.1%).