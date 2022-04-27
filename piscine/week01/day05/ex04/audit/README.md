##### The exercice is validated is all questions of the exercice are validated

###### Have the missing values and data types been checked ? 
###### Have the string dates been converted to datetime type ? 
###### Have the dates been set as index ? 
###### Have `info` or/and `describe` been used to have a first look at the data ?



**My results can be reproduced using: `np.random.seed = 2712`. Given the versions of NumPy used I do not guaranty the reproducibility of the results - that is why I also explain the steps to get to the solution.**

##### The question 1 is validated if the return is computed as: Return(t) = (Price(t+1) - Price(t))/Price(t) and returns this output. Note that if the index is not ordered in ascending order the futur return computed is wrong. The answer is also accepted if the returns is computed  as in the exercise 2 and then shifted in the futur using `shift`, but I do not recommend this implementation as it adds missing values !

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

    An example of solution is:

    ```python
        def compute_futur_return(price):
        return (price.shift(-1) - price)/price

        compute_futur_return(df['Adj Close'])
    ```


##### The question 2 is validated if the index of the Series is the same as the index of the DataFrame. The data of the series can be generated using `np.random.randint(0,2,len(df.index)`.

##### This question is validated if the Pnl is computed as: signal * futur_return. Both series should have the same index.

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

##### The question 4 is validated if the return of the strategy is computed as: `(Total earned - Total invested) / Total` invested. The result should be close to 0. The formula given could be simplified as `(PnLs.sum())/signal.sum()`. My return is: 0.00043546984088551553 because I invested 5147$ and I earned 5149$.

##### The question is validated if the previous signal Series is replaced with 1s. Similarly as the previous question, we earned 10128$ and we invested 10118$ which leads to a return of 0.00112670194140969 (0.1%).
