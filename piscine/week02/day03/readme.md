# W2D01  Piscine AI - Data Science

## Machine Learning Pipeline

Today we will focus on the data preprocessing and discover the Pipeline object from scikit learn.

1. Manage categorical variables with Integer encoding and One Hot Encoding
2. Impute the missing values
3. Reduce the dimension of the data
4. Scale the data

- The **step 1** is always necessary. Models use numbers, for instance string data can't be processed raw.
- The **steps 2** is always necessary. Machine learning models use numbers, missing values do not have mathematical representations, that is why the missing values have to be imputed.
- The **step 3** is required when the dimension of the data set is high. The dimension reduction algorithms reduce the dimensionality of the data either by selecting the variables that contain most of the information (SelectKBest) or by transforming the data. Depending on the signal in the data and the data set size the dimension reduction is not always required. This step is not covered because of its complexity. The understanding of the theory behind is important. However, I suggest to give it a try during the projects.

- The **step 4** is required when using some type of Machine Learning algorithms. The Machine Learning algorithms that require the feature scaling are mostly KNN (K-Nearest Neighbors), Neural Networks, Linear Regression, and Logistic Regression. The reason why some algorithms work better with feature scaling is that the minimization of the loss function may be more difficult if each feature's range is completely different. 

These steps are sequential. The output of step 1 is used as input for step 2 and so on; and, the output of step 4 is used as input for the Machine Learning model.
Scikitlearn proposes an object: Pipeline.

As we know, the model evaluation methodology requires to split the data set in a train set and test set. **The preprocessing is learned/fitted on the training set and applied on the test set**.

This object takes as input the preprocessing transforms and a Machine Learning model. Then this object can be called the same way a Machine Learning model is called. This is pretty practical because we do not need anymore to carry many objects.

## Exercises of the day

- Exercise 1 Imputer 1
- Exercise 2 Scaler
- Exercise 3 One hot Encoder
- Exercise 4 Ordinal Encoder
- Exercise 5 Categorical variables
- Exercise 6 Pipeline


## Virtual Environment 
- Python 3.x
- NumPy
- Pandas
- Matplotlib
- Scikit Learn
- Jupyter or JupyterLab

*Version of Scikit Learn I used to do the exercises: 0.22*. I suggest to use the most recent one. Scikit Learn 1.0 is finally available after ... 14 years. 

## Ressources

### Step 3

- https://towardsdatascience.com/dimensionality-reduction-for-machine-learning-80a46c2ebb7e

### Step 4

- https://medium.com/@societyofai/simplest-way-for-feature-scaling-in-gradient-descent-ae0aaa383039#:~:text=Feature%20scaling%20is%20an%20idea,of%20convergence%20of%20gradient%20descent.

### Pipeline 

- https://scikit-learn.org/stable/modules/generated/sklearn.pipeline.Pipeline.html