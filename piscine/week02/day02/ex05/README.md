# Exercise 5 Breast Cancer prediction

The goal of this exercise is to use Logistic Regression
to predict breast cancer. It is always important to understand the data before training any Machine Learning algorithm. The data is described in **breast-cancer-wisconsin.names**. I suggest to add manually the column names in the DataFrame.

Preliminary:

- If needed, replace missing values with the median of the column.

- Handle the column `Sample code number`. This column won't be used to train the model as it doesn't contain information on breast cancer. There are two solutions: drop it or set it as index.

1. Print the proportion of class `Benign`.  What would be the accuracy if the model always predicts `Benign`?
Later this week we will learn about other metrics as AUC that will help us to tackle high imbalanced data sets.

2. Using train_test_split, split the data set in a train set and test set (20%). Both sets should have approximately the same proportion of class `Benign`. Use `random_state = 43`.

3. Fit the logistic regression on the train set. Predict on the train set and test set. Compute the score on the train set and test set. 92-97% accuracy is expected on the test set.

4. Compute the confusion matrix on both tests. Analyse the number of false negative and false positive.

- https://scikit-learn.org/stable/modules/generated/sklearn.metrics.confusion_matrix.html

- https://archive.ics.uci.edu/ml/machine-learning-databases/breast-cancer-wisconsin/
