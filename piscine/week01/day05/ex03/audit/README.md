##### This question is validated if, without having used a for loop, the outputted DataFrame shape's `(261, 5)` and the output is the same as the one return with this line of code. The DataFrame contains random data. Make sure the output and the one returned by this code is based on the same DataFrame.

    ```python
    market_data.loc[market_data.index.get_level_values('Ticker')=='AAPL'].sort_index().pct_change()
    ```

