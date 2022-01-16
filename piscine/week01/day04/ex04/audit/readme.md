##### The exercice is validated is all questions of the exercice are validated and if the for loop hasn't been used. The goal is to use `groupby` and `apply`.

##### The question 1 is validated if the output is:

    ```python
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

##### The question 2 is validated if the output is a Pandas Series or DataFrame with the first 11 rows equal to the output below. The code below give a solution. 

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


    ```python
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

- https://towardsdatascience.com/how-to-use-the-split-apply-combine-strategy-in-pandas-groupby-29e0eb44b62e
