1. The question is validated if the output is:

| product      |   ('value', 'min') |   ('value', 'max') |   ('value', 'mean') |
|:-------------|-------------------:|-------------------:|--------------------:|
| chair        |              22.89 |              32.12 |              27.505 |
| mobile phone |             100    |             111.22 |             105.61  |
| table        |              20.45 |              99.99 |              51.22  |

Note: The columns don't have to be MultiIndex

My answer is: `df.groupby('product').agg({'value':['min','max','mean']})`