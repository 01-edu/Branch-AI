# Exercise 4 Groupby Apply

The goal of this exercise is to learn to group the data and apply a function on the groups.
The use case we will work on is computing

1. Create a function that uses `pandas.DataFrame.clip` and that replace extreme values by a given percentile. The values that are greater than the upper percentile 80% are replaced by the percentile 80%. The values that are smaller than the lower percentile 20% are replaced by the percentile 20%. This process that correct outliers is called **winsorizing**.
I recommend to use NumPy to compute the percentiles to make sure we used the same default parameters.

    ```python
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

2. Now we consider that each value belongs to a group. The goal is to apply the **winsorizing to each group**. In this question we use winsorizing values that are common: `[0.05,0.95]` as percentiles. Here is the new data set:

    ```python
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
