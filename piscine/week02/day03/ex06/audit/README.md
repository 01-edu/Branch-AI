##### The question 1 is validated if the prediction on the test set are:

```console
array([0, 0, 2, 1, 2, 0, 2, 1, 1, 1, 0, 1, 2, 0, 1, 1, 0, 0, 2, 2, 0, 0,
       0, 2, 2, 2, 0, 1, 0, 0, 1, 0, 1, 1, 2, 2, 1, 2, 1, 1, 1, 2, 1, 2,
       0, 1, 1, 1, 1, 1])
```

and the score on the test set is **98%**.

**Note: Keep in mind that having a 98% accuracy is not common when working with real life data. Every time you have a score > 97% check that there's no leakage in the data. On financial data set, the ratio signal to noise is low. Trying to forecast stock prices is a difficult problem. Having an accuracy higher than 70% should be interpreted as a warning to check data leakage !**
