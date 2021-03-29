# D02  Piscine AI - Data Science 


# Table of Contents:


# Introduction

Machine learning algorithms cannot work with raw text directly. Rather, the text must be converted into vectors of numbers. In natural language processing, a common technique for extracting features from text is to place all of the words that occur in the text in a bucket. This aproach is called a bag of words model or BoW for short. It’s referred to as a “bag” of words because any information about the structure of the sentence is lost.

Almost every Natural Language Processing (NLP) task requires text to be preprocessed before training a model. Deep learning models cannot use raw text directly, so it is up to us researchers to clean the text ourselves. Depending on the nature of the task, the preprocessing methods can be different. 

https://towardsdatascience.com/your-guide-to-natural-language-processing-nlp-48ea2511f6e1


The algorithms do not understand words. They need a mathematical reprensation of them. 
Today we will learn two important mathematical representations: 

- Bag of Words
- Embedding

Each approach has its limits. Context .. 

Les packages NLTK and Spacy to do the preprocessing



## Rules

## Ressources 

# Exercice 1: Lowercase

The goal of this exercice is to learn to lowercase text data in Python. Note that if the volume of data is low the text data can be stored in a Pandas DataFrame or Series. But, when dealing with high volumes (high but not huge), using a Pandas DataFrame or Series is not efficient. Data structures as dictionaries or list are more adapted. 

```
list_ = ["This is my first NLP exercice", "wtf!!!!!"]
series_data = pd.Series(list_, name='text')

```
1. Print all texts in lowercase
2. Print all texts in upper case

Note: Do not change the text manually ! 
## Correction

1. This question is validated if the output is: 
    ```
    0    this is my first nlp exercice
    1                         wtf!!!!!
    Name: text, dtype: object
    ```

2. This question is validated if the output is: 
    ```
    0    THIS IS MY FIRST NLP EXERCICE
    1                         WTF!!!!!
    Name: text, dtype: object
    ```

# Exerice 2: Punctation

The goal of this exerice is to learn to deal with punctuation. In Natural Language Processing, some basic approaches as Bag of Words (exercice X) model the text as an unordered combination of words. In that case the punctuation is not always useful as it doesn't add information to the model. That is why is removed. 

1. Remove the punctuation from this sentence. All characters in !"#$%&'()*+,-./:;<=>?@[\]^_`{|}~ are considered as punctuation.

    ```

    Remove, this from .? the sentence !!!! !"#&'()*+,-./:;<=>_

    ```

## Correction

1. This question is validated if the ouptut is: 


    ```

    Remove this from  the sentence

    ```

# Exercice 3 Tokenization

The goal of this exercice is to learn to tokenize as text. This step is important because it splits the text into token. A token could be a sentence or a word. 

```
text = """Bitcoin is a cryptocurrency invented in 2008 by an unknown person or group of people using the name Satoshi Nakamoto. The currency began use in 2009 when its implementation was released as open-source software."""

```
1. Tokenize this text using `sent_tokenize` from NLTK.

2. Tokenize this text using `word_tokenize` from NLTK.

*Ressource*: 
https://www.analyticsvidhya.com/blog/2019/07/how-get-started-nlp-6-unique-ways-perform-tokenization/

## Correction

1. This question is validated if the ouptut is: 


    ```

    ['Bitcoin is a cryptocurrency invented in 2008 by an unknown person or group of people using the name Satoshi Nakamoto.',
    'The currency began use in 2009 when its implementation was released as open-source software.']

    ```

2. This question is validated if the ouptut is: 


    ```

    ['Bitcoin',
    'is',
    'a',
    'cryptocurrency',
    'invented',
    'in',
    '2008',
    'by',
    'an',
    'unknown',
    'person',
    'or',
    'group',
    'of',
    'people',
    'using',
    'the',
    'name',
    'Satoshi',
    'Nakamoto',
    '.',
    'The',
    'currency',
    'began',
    'use',
    'in',
    '2009',
    'when',
    'its',
    'implementation',
    'was',
    'released',
    'as',
    'open-source',
    'software',
    '.']

    ```

# Exercice 4 Stop words

The goal of this exercice is to learn to remove stop words with NLTK.  Stop words usually refers to the most common words in a language. For example: "and", "is", "a" are stop words and do not add information to a sentence. 

```
text = """
The goal of this exercice is to learn to remove stop words with NLTK.  Stop words usually refers to the most common words in a language.
"""
```
1. Remove stop words from this sentence and return the list of work tokens without stop words. 


## Correction

1. This question is validated if, using NLTK, the ouptut is:
    ```
    ['The', 'goal', 'exercice', 'learn', 'remove', 'stop', 'words', 'NLTK', '.', 'Stop', 'words', 'usually', 'refers', 'common', 'words', 'language', '.']

    ```

# Exercice 5 Stemming

The goal of this exercice is to learn to use stemming using NLTK. As explained in details in the article, stemming is the process of reducing inflection in words to their root forms such as mapping a group of words to the same stem even if the stem itself is not a valid word in the Language. 

Note: The output of a stemmer is a word that may not exist in the dictionnary. 

```
text = """
The interviewer interviews the president in an interview 
"""
```

1. Return the list of tokens stemmed. 

## Correction

1. This question is validated if using NLTK, the output is: 

    ```
    ['the', 'interview', 'interview', 'the', 'presid', 'in', 'an', 'interview']

    ```


# Exercice 6: Text preprocessing

The goal of this exercice is to learn to create a function to prepocess and clean a text using NLTK. 


Put this text in a variable: 

```
01 Edu System presents an innovative curriculum in software engineering and programming. With a renowned industry-leading reputation, the curriculum has been rigorously designed for learning skills of the digital world and technology industry. Taking a different approach than the classic teaching methods today, learning is facilitated through a collective and co-créative process in a professional environment.

```

1. Write a function that takes as input the text and returns it preprocessed. 

The preprocessing is composed of:

    1. Lowercase
    2. Removing Punctuation
    3. Tokenization
    4. Stopword Filtering
    5. Stemming




https://towardsdatascience.com/nlp-preprocessing-with-nltk-3c04ee00edc0

## Correction

1. The question is validated if the output is: 


```
['01',
 'edu',
 'system',
 'present',
 'innov',
 'curriculum',
 'softwar',
 'engin',
 'program',
 'renown',
 'industrylead',
 'reput',
 'curriculum',
 'rigor',
 'design',
 'learn',
 'skill',
 'digit',
 'world',
 'technolog',
 'industri',
 'take',
 'differ',
 'approach',
 'classic',
 'teach',
 'method',
 'today',
 'learn',
 'facilit',
 'collect',
 'cocré',
 'process',
 'profession',
 'environ']

```

# Exercice 7: Bag of Word representation 

https://machinelearningmastery.com/gentle-introduction-bag-words-model/

The goal of this exercice is to understand how to create a Bag of Word (BoW) model on a corpus of texts. More precesily we will create a labeled data set from textual data using a word count matrix. 
As explained in the ressource, the Bag of word reprensation makes the assumption that the order in which the words appear in a text doesn't matter. There are different types of Bag of words reprensations: 

- Boolean: Each document is a boolean vector
- Wordcount: Each document is a word count vector
- TFIDF: Each document is a score vector. The score is detailed in the next exercice. 

The data `tweets_train.txt` contains tweets labeled with a sentiment. It gives the positivity of a tweet. 

Steps: 

1. Preprocess the data using the function implemented in the previous exercice. And, using from `CountVectorizer` of scikitlearn with `max_features=500` compute the wordcount of the tweets. The output is a sparse matrix.
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

https://scikit-learn.org/stable/modules/generated/sklearn.feature_extraction.text.CountVectorizer.html

## Correction

1. This question is validated if the output of the CountVectorizer is 

```
<6588x500 sparse matrix of type '<class 'numpy.int64'>'
	with 79709 stored elements in Compressed Sparse Row format>
```


2. This question is validated if the output of `print(df.iloc[:3,400:403].to_markdown())` is:


    |    |   talk |   team |   tell |
    |---:|-------:|-------:|-------:|
    |  0 |      0 |      0 |      0 |
    |  1 |      0 |      0 |      0 |
    |  2 |      0 |      0 |      0 |



3. This question is validated if the shape of the wordcount DataFrame `(6588, 501)` is and if the output of `print(df.iloc[300:304,499:501].to_markdown())` is:

    |     |   youtube |   label |
    |----:|----------:|--------:|
    | 300 |         0 |       0 |
    | 301 |         0 |      -1 |
    | 302 |         1 |       0 |
    | 303 |         0 |       1 |



