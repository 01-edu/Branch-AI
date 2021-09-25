# Exercice 4 Handling missing values

The goal of this exercise is to learn to handle missing values. In the previous exercise we used the first techniques: filter out the missing values. We were lucky because the proportion of missing values was low. But in some cases, dropping the missing values is not possible because the filtered data set would be too small.

This article explains the different types of missing data and how they should be handled.

https://towardsdatascience.com/data-cleaning-with-python-and-pandas-detecting-missing-values-3e9c6ebcf78b

"**It’s important to understand these different types of missing data from a statistics point of view. The type of missing data will influence how you deal with filling in the missing values.**"

- Preliminary: Drop the `flower` column

1. Fill the missing values with a different "strategy" for each column:

    `sepal_length` -> `mean`

    `sepal_width` -> `median`

    `petal_length`, `petal_width` -> `0`

2. Fill the missing values using the median of the associated column using `fillna`.


- Bonus questions: 
    - Filling the missing values by 0 or the mean of the associated column is common in Data Science. In that case, explain why filling the missing values with 0 or the mean is a bad idea.
    - Find a special row ;-)
