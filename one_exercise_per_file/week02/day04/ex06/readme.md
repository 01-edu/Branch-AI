# Exercise 6 Grid Search

The goal of this exercise is to learn how to make an exhaustive search over specified parameter values for an estimator. This is very useful because the hyperparameter which are the parameters of the model impact the performance of the model.

The scikit learn object that runs the Grid Search is called GridSearchCV. We will learn tomorrow about the cross validation. For now, let us set the parameter **cv** to `[(np.arange(18576), np.arange(18576,20640))]`.
This means that GridSearchCV splits the data set in a train and test set.

Preliminary:

- Load the California Housing data set. As precised, this time, there's no need to split the data set in train set and test set since GridSearchCV does it.

You will have to run a Grid Search on the Random Forest on at least the hyperparameter that are mentioned below. It doesn't mean these are the only hyperparameter of the model. If possible, try at least 3 different values for each hyperparameter.

1. Run a Grid Search with `n_jobs` set to `-1` to parallelize the computations on all CPUs. The hyperparameter to change are: n_estimators, max_depth, min_samples_leaf. It may take

Now, let us analyse the grid search's results in order to select the best model.

2. Write a function that takes as input the Grid Search object and that returns the best model **fitted**, the best set of hyperparameter and the associated score:

    ```python
    def select_model_verbose(gs):

        return trained_model, best_params, best_score
    ```

3. Use the trained model to predict on a new point:

```python
new_point = np.array([[3.2031, 52., 5.47761194, 1.07960199, 910., 2.26368159, 37.85, -122.26]])
```

How do we know the best model returned by GridSearchCV is good enough and stable ? That is what we will learn tomorrow !

**WARNING: Some combinations of hyper parameters are not possible. For example using the SVM, the kernel linear has no parameter gamma.**

**Note**:

- GridSearchCV can also take a Pipeline instead of a Machine Learning model. It is useful to combine some Imputers or Dimension reduction techniques with some Machine Learning models in the same Pipeline.
- It may be useful to check on Kaggle if some Kagglers share their Grid Searches.

Ressources:

- https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.GridSearchCV.html

- https://stackoverflow.com/questions/38555650/try-multiple-estimator-in-one-grid-search

- https://medium.com/fintechexplained/what-is-grid-search-c01fe886ef0a

- https://elutins.medium.com/grid-searching-in-machine-learning-quick-explanation-and-python-implementation-550552200596

- https://scikit-learn.org/stable/auto_examples/model_selection/plot_grid_search_digits.html