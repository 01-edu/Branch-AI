1. This question is validated if the output of the Ordinal Encoder on the train set is:

```console
array([[2.],
       [0.],
       [1.]])
```

Check that `enc.categories_` returns`[array(['bad', 'neutral', 'good'], dtype=object)]`.

2. This question is validated if the output of the Ordinal Encoder on the test set is:

```console
array([[2.],
       [2.],
       [0.]])
```