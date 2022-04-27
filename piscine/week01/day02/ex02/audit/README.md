##### The exercice is validated is all questions of the exercice are validated

##### The solution of question 1 is accepted if `drop` is used with `axis=1`.`inplace=True` may be useful to avoid to affect the result to a variable. A solution that could be accepted too (even if it's not a solution I recommend) is `del`. 

##### The solution of question 2 is accepted if the DataFrame returns the output below. If the type of the index is not `dtype='datetime64[ns]'` the solution is not accepted. I recommend to use  `set_index` with `inplace=True` to do so. 

    ```python
        Input: df.head().index

        Output: 

        DatetimeIndex(['2006-12-16', '2006-12-16','2006-12-16', '2006-12-16','2006-12-16'],
        dtype='datetime64[ns]', name='Date', freq=None)
    ```

##### The solution of question 3 is accepted if all the types are `float64` as below. The preferred solution is `pd.to_numeric` with `coerce=True`. 

    ```python
        Input: df.dtypes

        Output: 

            Global_active_power      float64
            Global_reactive_power    float64
            Voltage                  float64
            Global_intensity         float64
            Sub_metering_1           float64
            dtype: object
                
    ```

##### The solution of question 4 is accepted if you use `df.describe()`.

##### The solution of question 5 is accepted if `dropna` is used and if the number of missing values is equal to 0. It is important to notice that 25979 rows contain missing values (for a total of 129895). `df.isna().sum()` allows to check the number of missing values and `df.dropna()` with `inplace=True` allows to remove the rows with missing values. 

##### The solution of question 6 is accepted if one of the two approaches below were used:

    ```python
        #solution 1
        df.loc[:,'A'] = (df['A'] + 1) * 0.06

        #solution 2
        df.loc[:,'A'] = df.loc[:,'A'].apply(lambda x: (x+1)*0.06)
                
    ```


    You may wonder `df.loc[:,'A']` is required and if `df['A'] = ...` works too. **The answer is no**. This is important in Pandas. Depending on the version of Pandas, it may return a warning. The reason is that you are affecting a value to a **copy** of the DataFrame and not in the DataFrame.
    More details: https://stackoverflow.com/questions/20625582/how-to-deal-with-settingwithcopywarning-in-pandas

##### The solution of question 7 is accepted as long as the output of `print(filtered_df.head().to_markdown())` is as below and if the number of rows is equal to **449667**.

    | Date                |   Global_active_power |   Global_reactive_power |
    |:--------------------|----------------------:|------------------------:|
    | 2008-12-27 00:00:00 |                 0.996 |                   0.066 |
    | 2008-12-27 00:00:00 |                 1.076 |                   0.162 |
    | 2008-12-27 00:00:00 |                 1.064 |                   0.172 |
    | 2008-12-27 00:00:00 |                 1.07  |                   0.174 |
    | 2008-12-27 00:00:00 |                 0.804 |                   0.184 |

##### The solution of question 8 is accepted if the output is

    ```console
        Global_active_power        0.254
        Global_reactive_power      0.000
        Voltage                  238.350
        Global_intensity           1.200
        Sub_metering_1             0.000
        Name: 2007-02-16 00:00:00, dtype: float64

    ```

##### The solution of question 9 if the output is `Timestamp('2009-02-22 00:00:00')`

##### The solution of question 10 if the output of `print(sorted_df.tail().to_markdown())` is

    | Date                |   Global_active_power |   Global_reactive_power |   Voltage |
    |:--------------------|----------------------:|------------------------:|----------:|
    | 2008-08-28 00:00:00 |                 0.076 |                       0 |    234.88 |
    | 2008-08-28 00:00:00 |                 0.076 |                       0 |    235.18 |
    | 2008-08-28 00:00:00 |                 0.076 |                       0 |    235.4  |
    | 2008-08-28 00:00:00 |                 0.076 |                       0 |    235.64 |
    | 2008-12-08 00:00:00 |                 0.076 |                       0 |    236.5  |

##### The solution of question 11 is accepted if the output is as below. The solution is based on `groupby` which creates groups based on the index `Date` and aggregates the groups using the `mean`.

    ```console
    Date
    2006-12-16    3.053475
    2006-12-17    2.354486
    2006-12-18    1.530435
    2006-12-19    1.157079
    2006-12-20    1.545658
                    ...   
    2010-12-07    0.770538
    2010-12-08    0.367846
    2010-12-09    1.119508
    2010-12-10    1.097008
    2010-12-11    1.275571
    Name: Global_active_power, Length: 1433, dtype: float64
    ```
