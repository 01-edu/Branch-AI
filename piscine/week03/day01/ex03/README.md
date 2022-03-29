# Exercise 3 Log loss

The goal of this exercise is to implement the Log loss function. As mentioned last week, this function is used in classification as a **loss function**. It means that the better the classifier is, the smaller the loss function is. W2D1, you implemented the gradient descent on the MSE loss to update the weights of the linear regression. Similarly, the minimization of the Log loss leads to finding optimal weights. 

Log loss: - 1/n * Sum[(y_true*log(y_pred) + (1-y_true)*log(1-y_pred))]

1. Create a function `log_loss_custom` and compute the loss for the data below: 

    ```
    y_true = np.array([0,1,1,0,1])
    y_pred = np.array([0.1,0.8,0.6, 0.5, 0.3])
    ```
    Check that `log_loss` from `sklearn.metrics` returns the same result
https://scikit-learn.org/stable/modules/generated/sklearn.metrics.log_loss.html