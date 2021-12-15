##### The question is validated if the output is as below. The columns don't have to be MultiIndex. A solution could be `df.groupby('product').agg({'value':['min','max','mean']})`


| product      |   ('value', 'min') |   ('value', 'max') |   ('value', 'mean') |
|:-------------|-------------------:|-------------------:|--------------------:|
| chair        |              22.89 |              32.12 |              27.505 |
| mobile phone |             100    |             111.22 |             105.61  |
| table        |              20.45 |              99.99 |              51.22  |
