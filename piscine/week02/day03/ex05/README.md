# Exercise 5 Categorical variables

The goal of this exercise is to learn how to deal with Categorical variables with Ordinal Encoder, Label Encoder and One Hot Encoder. For this exercice I strongly suggest to use a recent version of `sklearn >= 0.24.1` to avoid issues with the Ordinal Encoder. 

Preliminary:

- Load the breast-cancer.csv file
- Drop `Class` column
- Drop NaN values
- Split the data in a train set and test set (test set size = 20% of the total size) with `random_state=43`.

1. Count the number of unique values per feature in the train set.

2. Identify the variables ordinal variables, nominal variables and the target. Compute a One Hot Encoder transformation on the test set for all categorical features (no ordinal) in the following order `['node-caps' , 'breast', 'breast-quad', 'irradiat']`. Here are the assumptions made on the variables:

```console
age: Ordinal
['90-99' > '80-89' > '70-79' > '60-69' > '50-59' > '40-49' > '30-39' > '20-29' > '10-19']

menopause: Ordinal
['ge40'> 'premeno' >'lt40']

tumor-size: Ordinal
['55-59' > '50-54' > '45-49' > '40-44' > '35-39' > '30-34' > '25-29' > '20-24' > '15-19' > '10-14' > '5-9' > '0-4']

inv-nodes: Ordinal 
['36-39' > '33-35' > '30-32' > '27-29' > '24-26' > '21-23' > '18-20' > '15-17' > '12-14' > '9-11' > '6-8' > '3-5' > '0-2']

node-caps: One Hot
['yes' 'no']

deg-malig: Ordinal
[3 > 2 > 1]

breast: One Hot 
['left' 'right']

breast-quad: One Hot 
['right_low' 'left_low' 'left_up' 'central' 'right_up']


irradiat: One Hot 
['recurrence-events' 'no-recurrence-events']
```

- Fit on the train set

- Transform the test set

Example of expected output:

```console
# One Hot encoder on: ['node-caps' , 'breast', 'breast-quad', 'irradiat']

input: ohe.transform(X_test[ohe_cols])[:10]
output:
array([[1., 0., 1., 0., 0., 1., 0., 0., 0., 1., 0.],
       [1., 0., 1., 0., 0., 1., 0., 0., 0., 1., 0.],
       [1., 0., 1., 0., 0., 0., 0., 1., 0., 1., 0.],
       [1., 0., 0., 1., 0., 1., 0., 0., 0., 1., 0.],
       [1., 0., 0., 1., 0., 0., 0., 1., 0., 1., 0.],
       [1., 0., 0., 1., 0., 0., 1., 0., 0., 1., 0.],
       [1., 0., 0., 1., 0., 0., 1., 0., 0., 1., 0.],
       [1., 0., 0., 1., 0., 1., 0., 0., 0., 1., 0.],
       [1., 0., 0., 1., 0., 0., 1., 0., 0., 1., 0.],
       [0., 1., 1., 0., 0., 0., 1., 0., 0., 0., 1.]])

input: ohe.get_feature_names(ohe_cols)
output: 
array(['node-caps_no', 'node-caps_yes', 'breast_left', 'breast_right',
       'breast-quad_central', 'breast-quad_left_low',
       'breast-quad_left_up', 'breast-quad_right_low',
       'breast-quad_right_up', 'irradiat_no', 'irradiat_yes'],
      dtype=object)

```

3. Create one Ordinal encoder for all Ordinal features in the following order `["menopause", "age", "tumor-size","inv-nodes", "deg-malig"]` on the test set. The documentation of Scikit-learn is not clear on how to perform this on many columns at the same time. Here's a **hint**:

If the ordinal data set is (subset of two columns but I keep all rows for this example):

    |    | menopause     |   deg-malig |
    |---:|:--------------|------------:|
    |  0 | premeno       |           3 |
    |  1 | ge40          |           1 |
    |  2 | ge40          |           2 |
    |  3 | premeno       |           3 |
    |  4 | premeno       |           2 |

The first step is to create a dictionnary or a list - the most recent version of sklearn take as input lists:

```console
dict_ = {0: ['lt40', 'premeno' , 'ge40'], 1:[1,2,3]}
```

Then to instantiate an `OrdinalEncoder`:

```console
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

```console
AttributeError: Transformer ordinalencoder (type OrdinalEncoder) does not provide get_feature_names.
```

**It means that if you want to use the Ordinal Encoder, you will have to create a variable that contains the columns name in the right order. This step is not required in that exercise**

Ressources:

- https://towardsdatascience.com/guide-to-encoding-categorical-features-using-scikit-learn-for-machine-learning-5048997a5c79

- https://machinelearningmastery.com/one-hot-encoding-for-categorical-data/
