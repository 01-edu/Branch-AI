##### The exercice is validated is all questions of the exercice are validated

##### The question 1 is validated if the output of is as below. The best solution uses `pd.date_range` to generate the index and `range` to generate the integer series.

    ```console
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

##### This question is validated if the output is as below. If the `NaN` values have been dropped the solution is also accepted. The solution uses `rolling().mean()`.

    ```console
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