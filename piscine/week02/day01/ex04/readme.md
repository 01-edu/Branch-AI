# Exercise 4 Forecast diabetes progression

The goal of this exercise is to use Linear Regression to forecast the progression of diabetes. It will not always be precised, you should **ALWAYS** start doing an exploratory data analysis in order to have a good understanding of the data you model. As a reminder here an introduction to EDA:

- https://towardsdatascience.com/exploratory-data-analysis-eda-a-practical-guide-and-template-for-structured-data-abfbf3ee3bd9

The data set used is described in https://scikit-learn.org/stable/modules/generated/sklearn.datasets.load_diabetes.

```python
from sklearn.datasets import load_diabetes
diabetes = load_diabetes()
X, y = diabetes.data, diabetes.target
```

1. Using `train_test_split`, split the data set in a train set, and test set (20%). Use `random_state=43` for results reproducibility.

2. Fit the Linear Regression on all the variables. Give the coefficients and the intercept of the Linear Regression. What is the the equation ?

3. Predict on the test set. Predicting on the test set is like having new patients for who, as a physician, need to forecast the disease progression in one year given the 10 baseline variables.

4. Compute the MSE on the train set and test set.  Later this week we will learn about the R2 which will help us to evaluate the performance of this fitted Linear Regression. The MSE returns an arbitrary value depending on the range of error.

**WARNING**: This will be explained later this week. But here, we are doing something "dangerous". As you may have read in the data documentation the data is scaled using the whole dataset whereas we should first scale the data on the training set and then use this scaling on the test set. This is a toy example, so let's ignore this detail for now.

https://scikit-learn.org/stable/datasets/toy_dataset.html#diabetes-dataset
