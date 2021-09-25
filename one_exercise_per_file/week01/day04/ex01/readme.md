# Exercise 1 Concatenate

The goal of this exercise is to learn to concatenate DataFrames. The logic is the same for the Series.

Here are the two DataFrames to concatenate:

```python
df1 = pd.DataFrame([['a', 1], ['b', 2]],
                   columns=['letter', 'number'])
df2 = pd.DataFrame([['c', 1], ['d', 2]],
                   columns=['letter', 'number'])
```

1. Concatenate this two DataFrames on index axis and reset the index. The index of the outputted should be `RangeIndex(start=0, stop=4, step=1)`. **Do not change the index manually**.
