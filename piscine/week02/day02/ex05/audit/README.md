##### The exercice is validated is all questions of the exercice are validated

##### The question 1 is validated if the proportion of class `Benign` is 0.6552217453505007. It means that if you always predict `Benign` your accuracy would be 66%.

##### The question 2 is validated if the proportion of one of the classes is the approximately the same on the train and test set: ~0.65. In my case:

- test: 0.6571428571428571
- train: 0.6547406082289803

##### The question 3 is validated if the output is:

```console
# Train
Class prediction on train set: 
 [4 2 4 2 2 2 2 4 2 2]

Probability prediction on train set: 
 [0.99600415 0.00908666 0.99992744 0.00528803 0.02097154 0.00582772
 0.03565076 0.99515326 0.00788281 0.01065484]

Score on train set: 
 0.9695885509838998

 #Test

 Class prediction on test set: 
 [2 2 2 4 2 4 2 2 2 4]

Probability prediction on test set: 
 [0.01747203 0.22495309 0.00698756 0.54020801 0.0015289  0.99862249
 0.33607994 0.01227679 0.00438157 0.99972344]

Score on test set: 
 0.9642857142857143

```

Only the 10 first predictions are outputted. The score is computed on all the data in the folds.
For some reasons, you may have a different data splitting as mine. The requirement for this question is to have a score on the test set bigger than 92%.

If the score is 1, congratulate you peer, he's just leaked his first target. The target should be dropped from the X_train or X_test ;) !

##### The question 4 is validated if the confusion matrix on the train set is similar to:

```console
array([[357,   9],
       [  8, 185]])
```

and if the confusion matrix on the test set is similar to:

```console
array([[90,  2],
       [ 3, 45]])
```

As said, for some reasons, the results may be slightly different from mine because of the data splitting. However, the values in the confusion matrix should be close to these results.
