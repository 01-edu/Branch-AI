##### The exercice is validated is all questions of the exercice are validated

##### The question 1 is validated if the outputted DataFrame's shape is `(1305, 5)` and if `merged.head()` returns a table as below. One of the answers that returns the correct DataFrame is `market_data.merge(alternative_data, how='left', left_index=True, right_index=True)`

|                                                      |       Open |     Close |   Close_Adjusted |     Twitter |    Reddit |
|:-----------------------------------------------------|-----------:|----------:|-----------------:|------------:|----------:|
| (Timestamp('2021-01-01 00:00:00', freq='B'), 'AAPL') |  0.0991792 | -0.31603  |         0.634787 | -0.00159041 |  1.06053  |
| (Timestamp('2021-01-01 00:00:00', freq='B'), 'FB')   | -0.123753  |  1.00269  |         0.713264 |  0.0142127  | -0.487028 |
| (Timestamp('2021-01-01 00:00:00', freq='B'), 'GE')   | -1.37775   | -1.01504  |         1.2858   |  0.109835   |  0.04273  |
| (Timestamp('2021-01-01 00:00:00', freq='B'), 'AMZN') |  1.06324   |  0.841241 |        -0.799481 | -0.805677   |  0.511769 |
| (Timestamp('2021-01-01 00:00:00', freq='B'), 'DAI')  | -0.603453  | -2.06141  |        -0.969064 |  1.49817    |  0.730055 |


##### The question 2 is validated if the numbers that are missing in the DataFrame are equal to 0 and if `filled_df.sum().sum() == merged_df.sum().sum()` gives: `True`
