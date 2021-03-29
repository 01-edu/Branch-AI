# W2D03  Piscine AI - Data Science 


# Table of Contents:


# Introduction

Today we will focus on the data preprocessing and discover the Pipeline object from scikit learn. 

1. Manage categorical variables with Integer encoding and One Hot Encoding 
2. Impute the missing values 
3. Reduce the dimension of the data 
4. Scale the data 



- The **step 1** is always necessary. Models use numbers, for instance string data can't be processed raw. 
- The **steps 2** is always necessary. Machine learning models use numbers, missing values do not have mathematical representations, that is why the missing values have to be imputed.  
- The **step 3** is required when the dimension of the data set is high. The dimension reduction algorithms reduce the dimensionality of the data either by selecting the variables that contain most of the information (SelectKBest) or by transforming the data. Depending on the signal in the data and the data set size the dimension reduction is not always required. This step is not covered because of its complexity. The understanding of the theory behind is important. However, I suggest to give it a try during the projects. This article gives an introduction. 
https://towardsdatascience.com/dimensionality-reduction-for-machine-learning-80a46c2ebb7e

- The **step 4** is required when using some type of Machine Learning algorithms. The Machine Learning algorithms that require the feature scaling are mostly KNN (K-Nearest Neighbours), Neural Networks, Linear Regression, and Logistic Regression. The reason why some algorithms work better with feature scaling is that the minimization of the loss function may be more difficult if each feature's range is completely different. More details: https://medium.com/@societyofai/simplest-way-for-feature-scaling-in-gradient-descent-ae0aaa383039#:~:text=Feature%20scaling%20is%20an%20idea,of%20convergence%20of%20gradient%20descent. 

These steps are sequential. The output of step 1 is used as input for step 2 and so on; and, the output of step 4 is used as input for the Machine Learning model. 
Scikitlearn proposes an object: Pipeline. 

As we know, the model evaluation methodology requires to split the data set in a train set and test set. **The preprocessing is learned/fitted on the training set and applied on the test set**.

https://scikit-learn.org/stable/modules/generated/sklearn.pipeline.Pipeline.html

This object takes as input the preprocessing transforms and a Machine Learning model. Then this object can be called the same way a Machine Learning model is called. This is pretty practical because we do not need anymore to carry many objects. 


## Ressources 
TODO

# Exercice 1 Imputer 1

The goal of this exercice is to learn how to use an Imputer to fill missing values on basic example.

```
train_data = [[7, 6, 5], 
              [4, np.nan, 5], 
              [1, 20, 8]]

```

1. Fit the `SimpleImputer` on the data. Print the `statistics_`. Check that the statistics match `np.nanmean(train_data, axis=0)`.

2. Fill the missing values in `train_data` using the fitted imputer and `transform`.
       
3. Fill the missing values in `test_data` using the fitted imputer and `transform`. 

```
test_data = [[np.nan, 1, 2], 
             [7, np.nan, 9], 
             [np.nan, 2, 4]]
```
  

## Correction 

1. This question is validated if the `imp_mean.statistics_` returns: 

    ```
    array([ 4., 13.,  6.])

    ```

2. This question is validated if the filled train set is: 

    ```
    array([[ 7.,  6.,  5.],
        [ 4., 13.,  5.],
        [ 1., 20.,  8.]])
    ```

3. This question is validated if the filled test set is: 

    ```
    array([[ 4.,  1.,  2.],
        [ 7., 13.,  9.],
        [ 4.,  2.,  4.]])
    ```

# Exercice 2 Scaler

The goal of this exercice is to learn to scale a data set. There are various scaling techniques, we will focus on `StandardScaler` from scikit learn. 

We will use a tiny data set for this exercice that we will generate by ourselves: 

``` 
X_train = np.array([[ 1., -1.,  2.],
                     [ 2.,  0.,  0.],
                     [ 0.,  1., -1.]])

```
1. Fit the `StandardScaler` on the data and scale X_train using `fit_transform`. Compute the `mean` and `std` on `axis 0 `.


2. Scale the test set using the `StandardScaler` fitted on the train set. 
``` 
X_test = np.array([[ 2., -1.,  1.],
                     [ 3.,  3.,  -1.],
                     [ 1.,  1., 1.]])

```

**WARNING: 
If the data is split in train and test set, it is extremely important to apply the same scaling the the test data. As the model is trained on scaled data, if it takes as input unscaled data, it returns incorrect values.**


Ressources: 

https://medium.com/technofunnel/what-when-why-feature-scaling-for-machine-learning-standard-minmax-scaler-49e64c510422

https://scikit-learn.org/stable/modules/preprocessing.html


## Correction

1. This question is validated if the scaled train set is:
```
array([[ 0.        , -1.22474487,  1.33630621],
       [ 1.22474487,  0.        , -0.26726124],
       [-1.22474487,  1.22474487, -1.06904497]])

```
- The mean on axis 0 should return:
    - array([0., 0., 0.])
- The std on axis 0 should return: 
    - array([1., 1., 1.])

2. This question is validated if the scaled test set is: 

```
array([[ 1.22474487, -1.22474487,  0.53452248],
       [ 2.44948974,  3.67423461, -1.06904497],
       [ 0.        ,  1.22474487,  0.53452248]])

```
# Exercice 3 One hot Encoder 
The goal of this exercice is to learn how to deal with Categorical variables using the OneHot Encoder. 

```
X_train = [['Python'], ['Java'], ['Java'], ['C++']]

```
1. Using `OneHotEncoder` with `handle_unknown='ignore'`, fit the One Hot Encoder and transform X_train. The expected output is:

    |    |   ('C++',) |   ('Java',) |   ('Python',) |
    |---:|-----------:|------------:|--------------:|
    |  0 |          0 |           0 |             1 |
    |  1 |          0 |           1 |             0 |
    |  2 |          0 |           1 |             0 |
    |  3 |          1 |           0 |             0 |

    To get this output create a DataFrame from the transformed X_train and the attribute `categories_`.


2. Transform X_test using the fitted One Hot Encoder on the train set. 

    ```
    X_test = [['Python'], ['Java'], ['C'], ['C++']]
    ```

    The expected output is:

    |    |   ('C++',) |   ('Java',) |   ('Python',) |
    |---:|-----------:|------------:|--------------:|
    |  0 |          0 |           0 |             1 |
    |  1 |          0 |           1 |             0 |
    |  2 |          0 |           0 |             0 |
    |  3 |          1 |           0 |             0 |

https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.OneHotEncoder.html


## Correction 

1. This question is validated if the output is 

    |    |   ('C++',) |   ('Java',) |   ('Python',) |
    |---:|-----------:|------------:|--------------:|
    |  0 |          0 |           0 |             1 |
    |  1 |          0 |           1 |             0 |
    |  2 |          0 |           1 |             0 |
    |  3 |          1 |           0 |             0 |

2. This question is validated if the output is: 

    |    |   ('C++',) |   ('Java',) |   ('Python',) |
    |---:|-----------:|------------:|--------------:|
    |  0 |          0 |           0 |             1 |
    |  1 |          0 |           1 |             0 |
    |  2 |          0 |           0 |             0 |
    |  3 |          1 |           0 |             0 |



# Exercice 4 Ordinal Encoder
The goal of this exercice is to learn how to deal with Categorical variables using the Ordinal Encoder. 

In that case, we want the model to consider that: **good > neutral > bad**


```
X_train = [['good'], ['bad'], ['neutral']]

```
1. Fit the `OrdinalEncoder` by specifying the categories in the following order: `categories=[['bad', 'neutral', 'good']]`. Transform the train set. Print the `categories_`


2. Transform the X_test using the fitted Ordinal Encoder on train set. 

```
X_test = [['good'], ['good'], ['bad']]

```
*Note: In the version 0.22 of Scikit-learn, the Ordinal Encoder doesn't handle new values in the test set. But it will be possible in the version 0.24 !* 

## Correction 

1. This question is validated if the output of the Ordinal Encoder on the train set is: 

```
array([[2.],
       [0.],
       [1.]])
```

Check that `enc.categories_` returns`[array(['bad', 'neutral', 'good'], dtype=object)]`.

2. This question is validated if the output of the Ordinal Encoder on the test set is: 

```
array([[2.],
       [2.],
       [0.]])
```



# Exercice 5 Categorical variables 

The goal of this exercice is to learn how to deal with Categorical variables with Ordinal Encoder, Label Encoder and OneHot Encoder. 

Preliminary:
- Load the breast-cancer.csv file
- Drop `Class` column
- Drop NaN values
- Split the data in a train set and test set (test set size = 20% of the total size) with `random_state=43`. 

1. Count the number of unique values per feature in the train set
2. Identify the variables ordinal variables, nominal variables and the target.  Create one One Hot Encoder for all categorical features (no ordinal). Here are the assumptions made on the variables: 


```
age: Ordinal
['ge40'> 'premeno' >'lt40']

menopause: Ordinal
['50-54' > '45-49' > '40-44' >  '35-39' > '30-34' > '25-29'> '20-24' > '15-19' > '10-14' > '5-9' > '0-4']

tumor-size: Ordinal
['15-17' >  '12-14' > '9-11' > '6-8' > '3-5' > '0-2']

inv-nodes: One Hot 
['yes' 'no']

node-caps: Ordinal
[3 > 2 > 1]

deg-malig: One Hot 
['left' 'right']

breast: One Hot 
['right_low' 'left_low' 'left_up' 'central' 'right_up']

breast-quad: One Hot 
['yes' 'no']

irradiat: One Hot 
['recurrence-events' 'no-recurrence-events']
```
- Fit on the train set
- Transform the test set 

    Example of expected output: 



```

# One Hot encoder on: ['inv-nodes', 'deg-malig', 'breast', 'breast-quad', 'irradiat']

input: ohe.transform(df[ohe_cols]) 
output:
array([[0., 1., 0., ..., 0., 0., 1.],
    [1., 0., 0., ..., 0., 1., 0.],
    [1., 0., 1., ..., 0., 0., 1.],
    ...,
    [0., 1., 0., ..., 0., 1., 0.],
    [1., 0., 0., ..., 0., 1., 0.],
    [1., 0., 1., ..., 0., 1., 0.]])

input: ohe.get_feature_names(ohe_cols)
output: 
array(['inv-nodes_no', 'inv-nodes_yes', 'deg-malig_left',
       'deg-malig_right', 'breast_central', 'breast_left_low',
       'breast_left_up', 'breast_right_low', 'breast_right_up',
       'breast-quad_no', 'breast-quad_yes',
       'irradiat_no-recurrence-events', 'irradiat_recurrence-events'],
      dtype=object)

```

3.  Create one Ordinal encoder for all Ordinal features. The documentation of Scikit-learn is not clear on how to perform this on many columns at the same time. Here's a **hint**:

If the ordinal data set is (subset of two columns but I keep all rows for this example):

    |    | age     |   node-caps |
    |---:|:--------|------------:|
    |  0 | premeno |           3 |
    |  1 | ge40    |           1 |
    |  2 | ge40    |           2 |
    |  3 | premeno |           3 |
    |  4 | premeno |           2 |

The first step is to create a dictionnary: 


```
dict_ = {0: ['lt40', 'premeno' , 'ge40'], 1:[1,2,3]}
```
Then to instantiate an `OrdinalEncoder`: 

```
oe = OrdinalEncoder(dict_)
```

Now that you have enough information:
- Fit on the train set
- Transform the test set 

4. Use a `make_column_transformer` to combine the two Encoders. 

- Fit on the train set
- Transform the test set 

*Hint: Check the first ressource* 


**Note: The version 0.22 of Scikit-learn can't handle `get_feature_names` on `OrdinalEncoder`. If the column transformer contains an `OrdinalEncoder`, the method returns this error**: 

```
AttributeError: Transformer ordinalencoder (type OrdinalEncoder) does not provide get_feature_names.

```

**It means that if you want to use the Ordinal Encoder, you will have to create a variable that contains the columns name in the right order. This step is not required in that exercice** 




Ressources: 

    https://towardsdatascience.com/guide-to-encoding-categorical-features-using-scikit-learn-for-machine-learning-5048997a5c79

    https://machinelearningmastery.com/one-hot-encoding-for-categorical-data/

## Correction 

1. This question is validated if the number of unique values per feature outputted are: 

```
age             3
menopause      11
tumor-size      7
inv-nodes       2
node-caps       3
deg-malig       2
breast          5
breast-quad     2
irradiat        2
dtype: int64
```


2. This question is validated if the transformed test set by the `OneHotEncoder` fitted on the train set is: 

    ```
    First 10 rows: 

    array([[1., 0., 1., 0., 0., 1., 0., 0., 0., 1., 0., 1., 0.],
        [1., 0., 1., 0., 0., 1., 0., 0., 0., 1., 0., 1., 0.],
        [0., 1., 1., 0., 0., 1., 0., 0., 0., 0., 1., 0., 1.],
        [0., 1., 1., 0., 0., 1., 0., 0., 0., 0., 1., 1., 0.],
        [1., 0., 1., 0., 0., 0., 1., 0., 0., 1., 0., 0., 1.],
        [1., 0., 1., 0., 0., 0., 0., 1., 0., 1., 0., 1., 0.],
        [1., 0., 0., 1., 0., 0., 0., 0., 1., 1., 0., 1., 0.],
        [1., 0., 0., 1., 0., 1., 0., 0., 0., 1., 0., 1., 0.],
        [1., 0., 1., 0., 0., 0., 0., 1., 0., 0., 1., 0., 1.],
        [1., 0., 0., 1., 0., 1., 0., 0., 0., 1., 0., 0., 1.]])
    ```

3. This question is validated if the transformed test set by the `OrdinalEncoder` fitted on the train set is: 

    ```
    First 10 rows: 

    array([[2., 2., 0., 1.],
        [2., 2., 0., 0.],
        [2., 4., 5., 2.],
        [1., 5., 1., 1.],
        [2., 5., 0., 2.],
        [1., 1., 0., 1.],
        [1., 8., 0., 1.],
        [2., 2., 0., 0.],
        [2., 5., 0., 2.],
        [1., 3., 0., 0.]])


    ```


4. This question is validated if the column transformer transformed that is fitted on the X_train, transformed the X_test as: 

```
# First 2 rows: 

array([[1., 0., 1., 0., 0., 1., 0., 0., 0., 1., 0., 1., 0., 2., 2., 0.,
        1.],
       [1., 0., 1., 0., 0., 1., 0., 0., 0., 1., 0., 1., 0., 2., 2., 0.,
        0.]])

```


# Exercice 6 Pipeline 

The goal of this exercice is to learn to use the Scikit-learn object: Pipeline. The data set: used for this exercice is the `iris` data set. 

Preliminary:
- Run the code below. 

    ```
    iris = load_iris()
    X, y = iris['data'], iris['target']

    #add missing values
    X[[1,20,50,100,135], 0] = np.nan
    X[[2,5,88,135], 1] = np.nan
    X[[4,15], 2] = np.nan
    X[[40,135], 3] = np.nan
    ```
- Split the data set in a train set and test set (33%), fit the Pipeline on the train set and predict on the test set. Use `random_state=43`.



The pipeline you will implement has to contain 3 steps: 

    - Imputer (median)
    - Standard Scaler
    - LogisticRegression


1. Train the pipeline on the train set and predict on the test set. Give the score of the model on the test set.  



## Correction 

1. This question is validated if the prediction on the test set are: 

```
array([0, 0, 2, 1, 2, 0, 2, 1, 1, 1, 0, 1, 2, 0, 1, 1, 0, 0, 2, 2, 0, 0,
       0, 2, 2, 2, 0, 1, 0, 0, 1, 0, 1, 1, 2, 2, 1, 2, 1, 1, 1, 2, 1, 2,
       0, 1, 1, 1, 1, 1])
```
and the score on the test set is **98%**. 


*Note: Keep in mind that having a 98% accuracy is not common on real life data. Every time you have a score > 97% check that there's no leakage in the data. 
On financial data set, the ratio signal to noise is low. Trying to forecast stock prices is a difficult problem. Having an accuracy higher than 70% should be interpreted as a warning to check data leakage !*





























# Exercice 1 Imputer 2

The goal of this exercice is to learn how to use an Imputer to fill missing values in the data set. 

**Reminder**: The data exploration should be done first. It tells which rows/variables should be removed because there are too many missing values. Then the remaining data points can be treated using an Imputer. 

More details: 

    - https://towardsdatascience.com/7-ways-to-handle-missing-values-in-machine-learning-1a6326adf79e

    - https://www.kaggle.com/dansbecker/handling-missing-values

- Load california_housing data set using fetch_california_housing  and store it two DataFrames: X_miss_california, y_miss_california. 
- Using this chunk add missing values to the data set.
    
```
import numpy as np
rng = np.random.RandomState(42)


def add_missing_values(X_full, y_full):
    n_samples, n_features = X_full.shape

    # Add missing values in 75% of the lines
    missing_rate = 0.75
    n_missing_samples = int(n_samples * missing_rate)

    missing_samples = np.zeros(n_samples, dtype=bool)
    missing_samples[: n_missing_samples] = True

    rng.shuffle(missing_samples)
    missing_features = rng.randint(0, n_features, n_missing_samples)
    X_missing = X_full.copy()
    X_missing[missing_samples, missing_features] = np.nan
    y_missing = y_full.copy()

    return X_missing, y_missing


X_miss_california, y_miss_california = add_missing_values(
    X_california, y_california)

```
- Remove rows with missing data on the target. 
- Compute the proportion of missing data per variable. 
- Split the data in a train set and a test set. The test set size is 20% of the total size of the data set after having removed the useless rows. 
- Use the SimpleImputer on the train set to fill the missing values with the median of each row. 
- Impute the missing values on the test set. 


https://scikit-learn.org/stable/modules/classes.html#module-sklearn.impute

This study shows the performance of different imputations techniques. During the projects it will be interesting to try these variations. 

https://scikit-learn.org/stable/auto_examples/impute/plot_missing_values.html#sphx-glr-auto-examples-impute-plot-missing-values-py