##### The exercice is validated is all questions of the exercice are validated

##### The question 1 is validated if the output of the CountVectorizer is 

```
<6588x500 sparse matrix of type '<class 'numpy.int64'>'
	with 79709 stored elements in Compressed Sparse Row format>
```


##### The question 2 is validated if the output of `print(df.iloc[:3,400:403].to_markdown())` is:


    |    |   talk |   team |   tell |
    |---:|-------:|-------:|-------:|
    |  0 |      0 |      0 |      0 |
    |  1 |      0 |      0 |      0 |
    |  2 |      0 |      0 |      0 |



##### The question 3 is validated if the shape of the wordcount DataFrame `(6588, 501)` is and if the output of `print(df.iloc[300:304,499:501].to_markdown())` is:

    |     |   youtube |   label |
    |----:|----------:|--------:|
    | 300 |         0 |       0 |
    | 301 |         0 |      -1 |
    | 302 |         1 |       0 |
    | 303 |         0 |       1 |


