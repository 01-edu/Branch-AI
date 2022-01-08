# W3D04  Piscine AI - Data Science

## Natural Language processing 

“NLP makes it possible for humans to talk to machines:” This branch of AI enables computers to understand, interpret, and manipulate human language. This technology is one of the most broadly applied areas of machine learning and is critical in effectively analyzing massive quantities of unstructured, text-heavy data.

Machine learning algorithms cannot work with raw text directly. Rather, the text must be converted into vectors of numbers. In natural language processing, a common technique for extracting features from text is to place all of the words that occur in the text in an unordered bucket. This aproach is called a bag of words model or BoW for short. It’s referred to as a “bag” of words because any information about the structure of the sentence is lost. This is useful to train usual machine learning models on text data. Other types of models as RNNs or LSTMs take as input a complete and ordered sequence. 

Almost every Natural Language Processing (NLP) task requires text to be preprocessed before training a model. The article **Your Guide to Natural Language Processing (NLP)** gives a very good introduction to NLP. 
 
Today, we  we will learn to preprocess text data and to create a bag of word representation. Les packages NLTK and Spacy to do the preprocessing


## Exercises of the day

- Exercise 1 Lower case 
- Exercise 2 Punctuation
- Exercise 3 Tokenization
- Exercise 4 Stop words
- Exercise 5 Stemming
- Exercise 6 Text preprocessing
- Exercise 7 Bag of Word representation

## Virtual Environment 
- Python 3.x
- Jupyter or JupyterLab
- Scikit Learn
- NLTK

I suggest to use the most recent libraries.

## Ressources

- https://towardsdatascience.com/your-guide-to-natural-language-processing-nlp-48ea2511f6e1

- https://towardsdatascience.com/word-embeddings-for-nlp-5b72991e01d4