# Exercise 5 Groupby Agg

The goal of this exercise is to learn to compute different type of aggregations on the groups. This small DataFrame contains products and prices.

|    |   value | product      |
|---:|--------:|:-------------|
|  0 |   20.45 | table        |
|  1 |   22.89 | chair        |
|  2 |   32.12 | chair        |
|  3 |  111.22 | mobile phone |
|  4 |   33.22 | table        |
|  5 |  100    | mobile phone |
|  6 |   99.99 | table        |

1. Compute the min, max and mean price for each product in one single line of code. The expected output is:

| product      |   ('value', 'min') |   ('value', 'max') |   ('value', 'mean') |
|:-------------|-------------------:|-------------------:|--------------------:|
| chair        |              22.89 |              32.12 |              27.505 |
| mobile phone |             100    |             111.22 |             105.61  |
| table        |              20.45 |              99.99 |              51.22  |

Note: The columns don't have to be MultiIndex