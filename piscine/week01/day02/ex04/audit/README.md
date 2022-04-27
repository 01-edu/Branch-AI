##### The exercice is validated is all questions of the exercice are validated (except the bonus question)

##### The solution of question 1 is accepted if the two steps are implemented in that order. First, convert the numerical columns to `float` and then fill the missing values. The first step may involve `pd.to_numeric(df.loc[:,col], errors='coerce')`. The second step is validated if you eliminated all missing values. However there are many possibilities to fill the missing values. Here is one of them:

    example:

    ```python
    df.fillna({0:df.sepal_length.mean(),
    2:df.sepal_width.median(),
    3:0,
    4:0})
    ```

##### The solution of question 2 is accepted if the solution is `df.loc[:,col].fillna(df[col].median())`.

######+ The solution of bonus question is accepted if you find out this answer: Once we filled the missing values as suggested in the first question, `df.describe()` returns this interesting summary. We notice that the mean is way higher than the median. It means that there are maybe some outliers in the data. The quantile 75 and the max confirm that: 75% of the flowers have a sepal length smaller than 6.4 cm, but the max is 6900 cm. If you check on the internet you realise this small flower can't be that big. The outliers have a major impact on the mean which equals to 56.9. Filling this value for the missing value is not correct since it doesn't correspond to the real size of this flower. That is why in that case the best strategy to fill the missing values is the median. The truth is that I modified the data set ! But real data sets ALWAYS contains outliers. Always think about the meaning of the data transformation ! If you fill the missing values by zero, it means that you consider that the length or width of some flowers may be 0. It doesn't make sense. 


|       |   sepal_length |   sepal_width |   petal_length |   petal_width |
|:------|---------------:|--------------:|---------------:|--------------:|
| count |       146      |      141      |       120      |      147      |
| mean  |        56.9075 |       52.6255 |        15.5292 |       12.0265 |
| std   |       572.222  |      417.127  |       127.46   |      131.873  |
| min   |        -4.4    |       -3.6    |        -4.8    |       -2.5    |
| 25%   |         5.1    |        2.8    |         2.725  |        0.3    |
| 50%   |         5.75   |        3      |         4.5    |        1.3    |
| 75%   |         6.4    |        3.3    |         5.1    |        1.8    |
| max   |      6900      |     3809      |      1400      |     1600      |



######+ The solution of bonus question is accepted if the presence of negative values and huge values have been detected. A good data scientist always check abnormal values in the dataset. **YOU SHOULD ALWAYS TRY TO UNDERSTAND YOUR DATA**. Print the row with index 122 ;-) This week, we will have the opportunity to focus on the data pre-processing to understand how the outliers can be handled.
