# Exercise 7: Bag of Word representation 

The goal of this exercise is to understand how to create a Bag of Word (BoW) model on a corpus of texts. More precesily we will create a labeled data set from textual data using a word count matrix. 

*Ressources: https://machinelearningmastery.com/gentle-introduction-bag-words-model/*

As explained in the ressource, the Bag of word reprensation makes the assumption that the order in which the words appear in a text doesn't matter. There are different types of Bag of words reprensations: 

- Boolean: Each document is a boolean vector
- Wordcount: Each document is a word count vector
- TFIDF: Each document is a score vector. The score is detailed in the next exercise. 

The data `tweets_train.txt` contains tweets labeled with a sentiment. It gives the positivity of a tweet. 

Steps: 

1. Preprocess the data using the function implemented in the previous exercise. And, using from `CountVectorizer` of scikitlearn with `max_features=500` compute the wordcount of the tweets. The output is a sparse matrix.
- Check the shape of the word count matrix
- Set **max_features** to 500 of the initial size of the dictionnary. 
        
        Reminder:  Given that a data set is often described as an m x n matrix in which m is the number of rows  and n is the number of columns: features.  It is strongly recommanded to work with m >> n. The value of the ratio depends on the signal existing in the data set and on the model complexity.
2. Using from_spmatrix from scikitlearn create a DataFrame with documents in rows and dictionary in columns.  

|    |   and |   boat |   compute |
|---:|------:|------------:|------:|
|  0 |     0 |           2 |     0 |
|  1 |     0 |           0 |     1 |
|  2 |     1 |           0 |     0 |

3. Create a dataframe with the labels
    - 1:  positive
    - 0:  neutral
    - -1: negative  

|    |   target |
|---:|------:|
|  0 |     -1 |
|  1 |     0 |
|  2 |     1 |

*Ressources: https://scikit-learn.org/stable/modules/generated/sklearn.feature_extraction.text.CountVectorizer.html*