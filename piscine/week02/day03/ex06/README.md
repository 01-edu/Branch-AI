# Exercise 6 Pipeline

The goal of this exercise is to learn to use the Scikit-learn object: Pipeline. The data set: used for this exercise is the `iris` data set.

Preliminary:

- Run the code below.

    ```console
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