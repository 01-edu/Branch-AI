
# Exercise 6 Multi-class (Optional)

The goal of this exercise is to learn to train a classification algorithm on a multi-class labelled data.
Some algorithms as SVM or Logistic Regression do not natively support multi-class (more than 2 classes). There are some approaches that allow to use these algorithms on multi-class data.
Let's assume we work with 3 classes: A, B and C.

- One-vs-Rest considers 3 binary classification problems: A vs B,C; B vs A,C and C vs A,B. If there are 10 classes, 10 binary classification problems would be fitted.
- One-vs-One considers 3 binary classification problems: A vs B, A vs C, B vs C. If there are 10 classes, 45 binary classification problems would be fitted. Given, the volume of data, this technique may not be scalable.

More details:

- https://machinelearningmastery.com/one-vs-rest-and-one-vs-one-for-multi-class-classification/

Let's implement the One-vs-Rest approach from `LogisticRegression`.

Preliminary:

- Import the Setosa data set from Scikit-learn

```python
from sklearn.datasets import load_iris
iris = load_iris()

X = pd.DataFrame(data=iris['data'], columns=iris.feature_names)
y = pd.DataFrame(data=iris['target'], columns=['target'])
```

- Using train_test_split, split the data set in a train set and test set (20%) with `shuffle=True` and `random_state=43`.

1. Create a function that takes as input the data and returns three **trained** classifiers.

- `clf0` takes as input a binary data set where the class 1 is `0` and class 0 is `1` and `2`.
- `clf1` takes as input a binary data set where the class 1 is `1` and class 0 is `0` and `2`.
- `clf2` takes as input a binary data set where the class 1 is `2` and class 0 is `0` and `1`.

```python
def train(X_train,y_train):
       #TODO
       return clf0, clf1, clf2
```

2. Create a function that takes as input the trained classifiers and the features set and that returns the predicted class. Use `predict_one_vs_all` to output the predicted classes on the test set. Compare the results with Logistic Regression algorithm from scikit learn used in One-vs-All mode. The results may change because the solver may not converge. Later this week, we will learn to preprocess the data to avoid convergence issues.

- `clf0` outputs the probability to belong to the class 1 which is `0`.
- `clf1` outputs the probability to belong to the class 1 which is `1`.
- `clf2` outputs the probability to belong to the class 1 which is `2`.

The predicted class is the one that gets the **highest probability** among the three models.

```python
def predict_one_vs_all(X, clf0, clf1, clf2 ):
       #TODO
       return classes
```

- https://randerson112358.medium.com/python-logistic-regression-program-5e1b32f964db

- https://towardsdatascience.com/logistic-regression-using-python-sklearn-numpy-mnist-handwriting-recognition-matplotlib-a6b31e2b166a
