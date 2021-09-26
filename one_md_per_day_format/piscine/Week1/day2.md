# D02  Piscine AI - Data Science

Author:

# Table of Contents:
Historical part:

# Introduction

The goal of this day is to understand practical usage of Pandas.
As Pandas in intensively used in Data Science, other days of the piscine will be dedicated to it.

Not only is the Pandas library a central component of the data science toolkit but it is used in conjunction with other libraries in that collection.

Pandas is built on top of the NumPy package, meaning a lot of the structure of NumPy is used or replicated in Pandas. Data in pandas is often used to feed statistical analysis in SciPy, plotting functions from Matplotlib, and machine learning algorithms in Scikit-learn.

Most of the topics we will cover today are explained and describes with examples in the first resource. The number of exercises is low on purpose: Take the time to understand the chapter 5 of the resource, even if there are 40 pages.

The version of Pandas I used is '1.0.1'.

## Rules

...

## Resources

- If I had to give you one resource it would be this one:

https://bedford-computing.co.uk/learning/wp-content/uploads/2015/10/Python-for-Data-Analysis.pdf

It contains ALL you need to know about Pandas.

- Pandas documentation:

  - https://pandas.pydata.org/docs/

  - https://jakevdp.github.io/PythonDataScienceHandbook/

  - https://pandas.pydata.org/Pandas_Cheat_Sheet.pdf

  - https://www.learndatasci.com/tutorials/python-pandas-tutorial-complete-introduction-for-beginners/

  - https://jakevdp.github.io/PythonDataScienceHandbook/03.04-missing-values.html

# Exercice 1 Your first DataFrame

The goal of this exercise is to learn to create basic Pandas objects.

1. Create a DataFrame as below this using two ways:
    - From a NumPy array
    - From a Pandas Series

    |    | color   | list    |   number |
    |---:|:--------|:--------|---------:|
    |  1 | Blue    | [1, 2]  |      1.1 |
    |  3 | Red     | [3, 4]  |      2.2 |
    |  5 | Pink    | [5, 6]  |      3.3 |
    |  7 | Grey    | [7, 8]  |      4.4 |
    |  9 | Black   | [9, 10] |      5.5 |

2. Print the types for every columns and the types of the first value of every columns

## Solution

1. The solution is accepted if the DataFrame created is the same as the "model" DataFrame. Check that the index is not 1,2,3,4,5.

2. The solution is accepted if the types you get for the columns are

    ```console
    <class 'pandas.core.series.Series'>
    <class 'pandas.core.series.Series'>
    <class 'pandas.core.series.Series'>
    ```

and if the types of the first value of the columns are

```console
    <class 'str'>
    <class 'list'>
    <class 'float'>
```

# Exercise 2  **Electric power consumption**

The goal of this exercise is to learn to manipulate real data with Pandas.

The data set used is **Individual household electric power consumption**

1. Delete the columns `Time`, `Sub_metering_2` and `Sub_metering_3`
2. Set `Date` as index
3. Create a function that takes as input the DataFrame with the data set and returns a DataFrame with updated types:

    ```python
        def update_types(df):
            #TODO
            return df
    ```

4. Use `describe` to have an overview on the data set
5. Delete the rows with missing values
6. Modify `Sub_metering_1` by adding 1 to it and multiplying the total by 0.06. If x is a row the output is: (x+1)*0.06
7. Select all the rows for which the Date is greater or equal than 2008-12-27 and `Voltage` is greater or equal than 242
8. Print the 88888th row.
9. What is the date for which the `Global_active_power` is maximal ?
10. Sort the first three columns by descending order of `Global_active_power` and ascending order of `Voltage`.
11. Compute the daily average of `Global_active_power`.

## Correction

1. `del` works but it is not a solution I recommend. For this exercise it is accepted. It is expected to use `drop` with `axis=1`. `inplace=True` may be useful to avoid to affect the result to a variable.

2. The preferred solution is `set_index` with `inplace=True`. As long as the DataFrame returns the output below, the solution is accepted. If the type of the index is not `dtype='datetime64[ns]'` the solution is not accepted.

    ```python
        Input: df.head().index

        Output: 

        DatetimeIndex(['2006-12-16', '2006-12-16','2006-12-16', '2006-12-16','2006-12-16'],
        dtype='datetime64[ns]', name='Date', freq=None)
    ```

3. The preferred solution is `pd.to_numeric` with `coerce=True`. The solution is accepted if all types are `float64`.

    ```python
        Input: df.dtypes

        Output: 

            Global_active_power      float64
            Global_reactive_power    float64
            Voltage                  float64
            Global_intensity         float64
            Sub_metering_1           float64
            dtype: object
                
    ```

4. `df.describe()` is expected

5. You should have noticed that 25979 rows contain missing values (for a total of 129895). `df.isna().sum()` allows to check the number of missing values and `df.dropna()` with `inplace=True` allows to remove the rows with missing values. The solution is accepted if you used `dropna` and have the number of missing values as 0.

6. Two solutions are accepted:
    - `df.loc[:,'A'] = (df['A'] + 1) * 0.06`
    - Using `apply`:  `df.loc[:,'A'] = df.loc[:,'A'].apply(lambda x: (x+1)*0.06)`

    You may wonder `df.loc[:,'A']` is required and if `df['A'] = ...` works too. The answer is no. This is important in Pandas. Depending on the version of Pandas, it may return a warning. The reason is that you are affecting a value to a **copy** of the DataFrame and not in the DataFrame.
    More details: https://stackoverflow.com/questions/20625582/how-to-deal-with-settingwithcopywarning-in-pandas

7. The solution is accepted as long as the output of `print(filtered_df.head().to_markdown())` is:

    | Date                |   Global_active_power |   Global_reactive_power |
    |:--------------------|----------------------:|------------------------:|
    | 2008-12-27 00:00:00 |                 0.996 |                   0.066 |
    | 2008-12-27 00:00:00 |                 1.076 |                   0.162 |
    | 2008-12-27 00:00:00 |                 1.064 |                   0.172 |
    | 2008-12-27 00:00:00 |                 1.07  |                   0.174 |
    | 2008-12-27 00:00:00 |                 0.804 |                   0.184 |

    Check that the number of rows is equal to **449667**.

8. The solution is accepted if output is

    ```console
        Global_active_power        0.254
        Global_reactive_power      0.000
        Voltage                  238.350
        Global_intensity           1.200
        Sub_metering_1             0.000
        Name: 2007-02-16 00:00:00, dtype: float64

    ```

9. The solution is accepted if the output is `Timestamp('2009-02-22 00:00:00')`

10. The solution is accepted if the output for `print(sorted_df.tail().to_markdown())` is

    | Date                |   Global_active_power |   Global_reactive_power |   Voltage |
    |:--------------------|----------------------:|------------------------:|----------:|
    | 2008-08-28 00:00:00 |                 0.076 |                       0 |    234.88 |
    | 2008-08-28 00:00:00 |                 0.076 |                       0 |    235.18 |
    | 2008-08-28 00:00:00 |                 0.076 |                       0 |    235.4  |
    | 2008-08-28 00:00:00 |                 0.076 |                       0 |    235.64 |
    | 2008-12-08 00:00:00 |                 0.076 |                       0 |    236.5  |

11. The solution is based on `groupby` which creates groups based on the index `Date` and aggregates the groups using the `mean`. The solution is accepted if the output is

    ```console
    Date
    2006-12-16    3.053475
    2006-12-17    2.354486
    2006-12-18    1.530435
    2006-12-19    1.157079
    2006-12-20    1.545658
                    ...   
    2010-12-07    0.770538
    2010-12-08    0.367846
    2010-12-09    1.119508
    2010-12-10    1.097008
    2010-12-11    1.275571
    Name: Global_active_power, Length: 1433, dtype: float64
    ```

# Exercice 3: E-commerce purchases<w>

The goal of this exercise is to learn to manipulate real data with Pandas. This exercise is less guided since the exercise 2 should have given you a nice introduction.

The data set used is **E-commerce purchases**.

Questions:

1. How many rows and columns are there?
2. What is the average Purchase Price?
3. What were the highest and lowest purchase prices?
4. How many people have English `'en'` as their Language of choice on the website?
5. How many people have the job title of `"Lawyer"` ?
6. How many people made the purchase during the `AM` and how many people made the purchase during `PM` ?
7. What are the 5 most common Job Titles?
8. Someone made a purchase that came from Lot: `"90 WT"` , what was the Purchase Price for this transaction?
9. What is the email of the person with the following Credit Card Number: `4926535242672853`
10. How many people have American Express as their Credit Card Provider and made a purchase above `$95` ?
11. How many people have a credit card that expires in `2025`?
12. What are the top 5 most popular email providers/hosts (e.g. gmail.com, yahoo.com, etc...)

## Correction

To validate this exercise all answers should return the expected numerical value given in the correction AND uses Pandas. For example using NumPy to compute the mean doesn't respect the philosophy of the exercise which is to use Pandas.

1. How many rows and columns are there?**10000 entries** and **14 columns**

    There many solutions based on: shape, info, describe

2. What is the average Purchase Price? **50.34730200000025**

    Even if `np.mean` gives the solution, `df['Purchase Price'].mean()` is preferred

3. What were the highest and lowest purchase prices?

    min: 0

    max: 99.989999999999995

4. How many people have English `'en'` as their Language of choice on the website? **1098**

5. How many people have the job title of `"Lawyer"` ? **30**

6. How many people made the purchase during the `AM` and how many people made the purchase during `PM` ?

    PM:    5068

    AM:    4932

    There many ways to the solution but the goal of this question was to make you use `value_counts`

7. What are the 5 most common Job Titles?

    Interior and spatial designer    31

    Lawyer                           30

    Social researcher                28

    Purchasing manager               27

    Designer, jewellery              27

    There many ways to the solution but the goal of this question was to make you use `value_counts`

8. Someone made a purchase that came from Lot: `"90 WT"` , what was the Purchase Price for this transaction? **75.1**
9. What is the email of the person with the following Credit Card Number: `4926535242672853`. **bondellen@williams-garza.com**
10. How many people have American Express as their Credit Card Provider and made a purchase above `$95` ? **39**

    The prefered solution is based on this:

    `df[(df['A'] == X) & (df['B'] > Y)]`
11. How many people have a credit card that expires in `2025`? **1033**

    The preferred solution is based on the usage of `apply` on a `lambda` function that slices the string that contains the expiration date.

12. What are the top 5 most popular email providers/hosts (e.g. gmail.com, yahoo.com, etc...)

    - hotmail.com     1638
    - yahoo.com       1616
    - gmail.com       1605
    - smith.com         42
    - williams.com      37

    The preferred solution is based on the usage of `apply` on a `lambda` function that slices the string that contains the email. The `lambda` function uses `split` to split the string on `@`. Finally, `value_counts` is used to count the occurrences.

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


## Correction

1. This question is validated if you have  done these two steps in that order:

- Convert the numerical columns to `float`

    example:

    ```python
    pd.to_numeric(df.loc[:,col], errors='coerce')
    ```

- Fill the missing values. There are many solutions for this step, here is one of them.

    example:

    ```python
    df.fillna({0:df.sepal_length.mean(),
    2:df.sepal_width.median(),
    3:0,
    4:0})
    ```


2. This question is validated if the solution is: `df.loc[:,col].fillna(df[col].median())`

**Bonus questions**:

- It is important to understand why filling the missing values with 0 or the mean of the column is a bad idea.

|       |   sepal_length |   sepal_width |   petal_length |   petal_width |
|:------|---------------:|--------------:|---------------:|--------------:|
| count |       146      |      141      |       120      |      147      |
| mean  |        56.9075 |       52.6255 |        15.5292 |       12.0265 |
| std   |       572.222  |      417.127  |       127.46   |      131.873  |
| min   |        -4.4    |       -3.6    |        -4.8    |       -2.5    |
| 25%   |         5.1    |        2.8    |         2.725  |        0.3    |
| 50%   |         5.75   |        3      |         4.5    |        1.3    |
| 75%   |         6.4    |        3.3    |         5.1    |        1.8    |
| max   |      6900      |     3809      |      1400      |     1600      |

Once we filled the missing values as suggested in the first question, `df.describe()` returns this interesting summary. We notice that the mean is way higher than the median. It means that there are maybe some outliers in the data. The quantile 75 and the max confirm that: 75% of the flowers have a sepal length smaller than 6.4 cm, but the max is 6900 cm. If you check on the internet you realise this small flower can't be that big. The outliers have a major impact on the mean which equals to 56.9. Filling this value for the missing value is not correct since it doesn't correspond to the real size of this flower. That is why in that case the best strategy to fill the missing values is the median. The truth is that I modified the data set ! But real data sets ALWAYS contains outliers.
Always think about the meaning of the data transformation ! If you fill the missing values by zero, it means that you consider that the length or width of some flowers may be 0. It doesn't make sense. 

- If you noticed that there are some negative values and the huge values, you will be a good data scientist. **YOU SHOULD ALWAYS TRY TO UNDERSTAND YOUR DATA**. Print the row with index 122 ;-)

This week, we will have the opportunity to focus on the data pre-processing to understand how the outliers are handled.

