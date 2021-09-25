# Exercise 5 Categorical variables

The goal of this exercise is to learn how to deal with Categorical variables with Ordinal Encoder, Label Encoder and One Hot Encoder.

Preliminary:

- Load the breast-cancer.csv file
- Drop `Class` column
- Drop NaN values
- Split the data in a train set and test set (test set size = 20% of the total size) with `random_state=43`.

1. Count the number of unique values per feature in the train set.

2. Identify the variables ordinal variables, nominal variables and the target. Create one One Hot Encoder for all categorical features (no ordinal). Here are the assumptions made on the variables:

```console
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

```console
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

3. Create one Ordinal encoder for all Ordinal features. The documentation of Scikit-learn is not clear on how to perform this on many columns at the same time. Here's a **hint**:

If the ordinal data set is (subset of two columns but I keep all rows for this example):

    |    | age     |   node-caps |
    |---:|:--------|------------:|
    |  0 | premeno |           3 |
    |  1 | ge40    |           1 |
    |  2 | ge40    |           2 |
    |  3 | premeno |           3 |
    |  4 | premeno |           2 |

The first step is to create a dictionnary:

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