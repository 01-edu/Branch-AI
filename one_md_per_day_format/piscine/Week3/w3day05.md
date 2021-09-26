# Week 3 D02  Piscine AI - Data Science 


# Table of Contents:


# Introduction

Embeddings ... 

Library: Spacy is a natural language processing (NLP) library for Python designed to have fast performance, and with word embedding models built in, it’s perfect for a quick and easy start.

There are many type of language models pre-trained in Spacy. Each has its specificities depending on the hypothesis taken. 
## Historical



## Rules

## Ressources 

# Exercise 1  Embedding 1

The goal of this exercise is to learn to load an embedding on SpaCy. 

1. Install and load `en_core_web_sm` embedding. Compute the embedding of `car`. 

## Correction 

1. This question is validated if the embedding's shape is `(96,)` 
and the vector 20 first values are: 

```
array([ 1.0522802e+00,  1.4806499e+00,  7.7402556e-01,  1.0373484e+00,
        4.1474584e-01, -5.7604712e-01,  3.0856287e+00,  1.4814860e-01,
       -3.0170975e+00,  3.4453702e+00,  6.3330579e-01,  1.1655847e+00,
        3.8489954e+00,  2.3469532e+00,  5.0532556e-01, -1.9386177e+00,
        9.7954911e-01,  2.3573284e+00, -1.9812435e-03,  5.5679207e+00],
      dtype=float32)

```

# Exercise 2: Tokenization


The goal of this exercise is to learn to tokenize a document using Spacy. We did this using NLTK yesterday. 

1. Tokenize the text below and print the tokens

    ```
        text = "Tokenize this sentence. And this one too."

    ```

## Correction 

1. The question is validated if the tokens printed are: 

    ```
    Tokenize
    this
    sentence
    .
    And
    this
    one
    too
    .
    ```

## Exercise 3  Embeddings 2

The goal of this exercise is to learn to use SpaCy embedding on a document. 

1. Compute the embedding of all the words in this sentence. The language model considered is `en_core_web_md`

``` 
"laptop computer coffee tea water liquid dog cat kitty"
``` 

2. Plot the pairwise cosine distances between all the words in a HeatMap.  
 
![alt text][logo]

[logo]: w3day05ex1_plot.png "Plot"

https://medium.com/datadriveninvestor/cosine-similarity-cosine-distance-6571387f9bf8


## Correction 

1. This question is validated if the embeddings of each word has a shape of `(300,)` and if the first 20 values of the embedding of laptop are:

    ```
    array([-0.37639 , -0.075521,  0.4908  ,  0.19863 , -0.11088 , -0.076145,
        -0.30367 , -0.69663 ,  0.87048 ,  0.54388 ,  0.42523 ,  0.18045 ,
        -0.4358  , -0.32606 , -0.70702 , -0.069127, -0.42674 ,  2.4147  ,
            0.26806 ,  0.46584 ], dtype=float32)

    ```

2. This question is validated if the output is 

![alt text][logo]

[logo]: w3day05ex1_plot.png "Plot"


# Exercise 4 Sentences' similarity 

The goal of this exerice is to learn to compute the similarity between two sentences. As explained in the documentation: **The word embedding of a full sentence is simply the average over all different words**. This is how `similarity` works in SpaCy. This small use case is very interesting because if we build a corpus of sentences that express an intention as **buy shoes**, then we can detect this intention and use it to propose shoes advertisement for customers. The language model used in this exercise is `en_core_web_sm`.


1. Compute the similarities (3 in total) between these sentences:

    ```
    sentence_1 = "I want to buy shoes"
    sentence_2 = "I would love to purchase running shoes"
    sentence_3 = "I am in my room"

    ```

## Correction 

1. This question is validated if the similarities between the sentences are: 

    ```
    sentence_1 <=> sentence 2 : 0.7073220863266589
    sentence_1 <=> sentence 3: 0.42663743263528325
    sentence_2 <=> sentence 3: 0.3336274235605957

    ```





# Exercise 5: NER

The goal of this exercise is to learn to use a Named entity recognition algorithm to detect entities. 

```
Apple Inc. is an American multinational technology company headquartered in Cupertino, California, that designs, develops, and sells consumer electronics, computer software, and online services. It is considered one of the Big Five companies in the U.S. information technology industry, along with Amazon, Google, Microsoft, and Facebook.
Apple was founded by Steve Jobs, Steve Wozniak, and Ronald Wayne in April 1976 to develop and sell Wozniak's Apple I personal computer, though Wayne sold his share back within 12 days. It was incorporated as Apple Computer, Inc., in January 1977, and sales of its computers, including the Apple I and Apple II, grew quickly.
 ```

1. Extract all named entities in the text as well as the label of the named entity.

2. The NER is also useful to remove ambigous entities. From a conceptual standpoint, disambiguation is the process of determining the most probable meaning of a specific phrase. For example in the sentence below, the word `apple` is present twice in the sentence. The first time to mention the fruit and the second to mention a company. Run the NER on this sentence and print the named entity, the `start_char`, the `end_char` and the label of the named entity. 

```
Paul eats an apple while watching a movie on his Apple device.
```
https://en.wikipedia.org/wiki/Named-entity_recognition
## Correction 

1. This question is validated if the ouptut of the NER is

    ```
    Apple Inc. ORG
    American NORP
    Cupertino GPE
    California GPE
    Five CARDINAL
    U.S. GPE
    Amazon ORG
    Google ORG
    Microsoft ORG
    Facebook ORG
    Apple ORG
    Steve Jobs PERSON
    Steve Wozniak PERSON
    Ronald Wayne PERSON
    April 1976 DATE
    Wozniak PERSON
    Apple ORG
    Wayne PERSON
    12 days DATE
    Apple Computer, Inc. ORG
    January 1977 DATE
    Apple ORG
    Apple II ORG
    ```
2. This question is validated if the output shows that the first occurence of apple is not a named entity. In my case here is what the NER returns: 

    ```
    Paul 1 5 PERSON
    Apple 50 55 ORG

    ```

# Exercise 6 Part-of-speech tags 

The goal od this exercise is to learn to use the Part-of-speech tags (**POS TAG**) using Spacy. As explained in wikipedia, the POS TAG is the process of marking up a word in a text (corpus) as corresponding to a particular part of speech, based on both its definition and its context.

Example

The sentence: **"Heat water in a large vessel"** is tagged this way after the POS TAG: 
- heat verb (noun)
- water noun (verb)
- in prep (noun, adv)
- a det (noun)
- large adj (noun)
- vessel noun


The data `news_amazon.txt` used is a news paper about Amazon. 

1. Return all sentences mentioning **Bezos** as a NNP (tag). 

## Correction 

1. This question is validated if the sentences outputed are: 

    ```
    INFO:  Bezos PROPN NNP
    Sentence:  Amazon (AMZN) enters 2021 with plenty of big opportunities, but is losing its lauded Chief Executive Jeff Bezos, who announced his plan to step aside in the third quarter.


    INFO:  Bezos PROPN NNP
    Sentence:  Bezos will hand off his role as chief executive to Andy Jassy, the CEO of its cloud computing unit.


    INFO:  Bezos PROPN NNP
    Sentence:  He's not leaving, as Bezos will transition to the role of Executive Chairman and remain active.


    INFO:  Bezos PROPN NNP
    Sentence:  "When you look at our financial results, what you're actually seeing are the long-run cumulative results of invention," Bezos said in written remarks with the Amazon earnings release.
    ```