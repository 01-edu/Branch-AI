##### The exercice is validated is all questions of the exercice are validated

##### The question 1 is validated if the predictions on the train set and test set are:

    ```console
    # 10 first values Train
    array([1, 0, 1, 1, 1, 0, 0, 1, 1, 0])

    # 10 first values Test
    array([1, 1, 0, 0, 0, 1, 1, 1, 0, 0])
    ```

##### The question 2 is validated if the results match this output:

```console
F1 on the train set:  0.9911504424778761
Accuracy on the train set:  0.989010989010989
Recall on the train set:  0.9929078014184397
Precision on the train set:  0.9893992932862191
ROC_AUC on the train set:  0.9990161111794368


F1 on the test set:  0.9801324503311258
Accuracy on the test set:  0.9736842105263158
Recall on the test set:  0.9866666666666667
Precision on the test set:  0.9736842105263158
ROC_AUC on the test set:  0.9863247863247864
```

##### The question 2 is validated if the results match the confusion matrix on the test set should be:

```console
array([[37,  2],
        [ 1, 74]])
```

##### The question 3 is validated if the ROC AUC plot looks like the plot below:

![alt text][logo_ex4]

[logo_ex4]: ../w2_day4_ex4_q3.png "ROC AUC "

Having a 99% ROC AUC is not usual. The data set we used is easy to classify. On real data sets, always check if there's any leakage while having such a high ROC AUC score.
