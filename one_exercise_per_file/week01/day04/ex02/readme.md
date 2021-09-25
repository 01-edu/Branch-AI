# Exercise 2 Merge

The goal of this exercise is to learn to merge DataFrames
The logic of merging DataFrames in Pandas is quite similar as the one used in SQL.

Here are the two DataFrames to merge:

```python
#df1

df1_dict = {
        'id': ['1', '2', '3', '4', '5'],
        'Feature1': ['A', 'C', 'E', 'G', 'I'],
        'Feature2': ['B', 'D', 'F', 'H', 'J']}

df1 = pd.DataFrame(df1_dict, columns = ['id', 'Feature1', 'Feature2'])

#df2
df2_dict = {
        'id': ['1', '2', '6', '7', '8'],
        'Feature1': ['K', 'M', 'O', 'Q', 'S'],
        'Feature2': ['L', 'N', 'P', 'R', 'T']}

df2 = pd.DataFrame(df2_dict, columns = ['id', 'Feature1', 'Feature2'])
```

1. Merge the two DataFrames to get this output:

    |    |   id | Feature1_x   | Feature2_x   | Feature1_y   | Feature2_y   |
    |---:|-----:|:-------------|:-------------|:-------------|:-------------|
    |  0 |    1 | A            | B            | K            | L            |
    |  1 |    2 | C            | D            | M            | N            |

2. Merge the two DataFrames to get this output:

    |    |   id | Feature1_df1   | Feature2_df1   | Feature1_df2   | Feature2_df2   |
    |---:|-----:|:---------------|:---------------|:---------------|:---------------|
    |  0 |    1 | A              | B              | K              | L              |
    |  1 |    2 | C              | D              | M              | N              |
    |  2 |    3 | E              | F              | nan            | nan            |
    |  3 |    4 | G              | H              | nan            | nan            |
    |  4 |    5 | I              | J              | nan            | nan            |
    |  5 |    6 | nan            | nan            | O              | P              |
    |  6 |    7 | nan            | nan            | Q              | R              |
    |  7 |    8 | nan            | nan            | S              | T              |

