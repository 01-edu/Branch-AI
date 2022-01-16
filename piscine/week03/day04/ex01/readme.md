# Exercise 1: Lowercase

The goal of this exercise is to learn to lowercase text data in Python. Note that if the volume of data is low the text data can be stored in a Pandas DataFrame or Series. But, when dealing with high volumes (high but not huge), using a Pandas DataFrame or Series is not efficient. Data structures as dictionaries or list are more adapted. 

```
list_ = ["This is my first NLP exercise", "wtf!!!!!"]
series_data = pd.Series(list_, name='text')

```
1. Print all texts in lowercase
2. Print all texts in upper case

Note: Do not change the text manually ! 