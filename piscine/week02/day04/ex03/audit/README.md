##### The exercice is validated is all questions of the exercice are validated

##### The question 1 is validated if the predictions on the train set and test set are:

```console
    #10 first values Train
array([1.54505951, 2.21338527, 2.2636205 , 3.3258957 , 1.51710076,
    1.63209319, 2.9265211 , 0.78080924, 1.21968217, 0.72656239])
    
```

```console
#10 first values Test

array([ 1.82212706,  1.98357668,  0.80547979, -0.19259114,  1.76072418,
        3.27855815,  2.12056804,  1.96099917,  2.38239663,  1.21005304])

```

#####  The question 2 is validated if the results match this output:

```console
r2 on the train set:  0.3552292936915783
MAE on the train set:  0.5300159371615256
MSE on the train set:  0.5210784446797679

r2 on the test set:  0.30265471284464673
MAE on the test set:  0.5454023699809112
MSE on the test set:  0.5537420654727396
```

This result shows that the model has slightly better results on the train set than the test set. That's frequent since it is easier to get a better grade on an exam we studied than an exam that is different from what was prepared. However, the results are not good: r2 ~ 0.3. Fitting non linear models as the Random Forest on this data may improve the results. That's the goal of the exercise 5.