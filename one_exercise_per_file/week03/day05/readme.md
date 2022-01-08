# W3D05  Piscine AI - Data Science

## Natural Language processing with Spacy 

Spacy is a natural language processing (NLP) library for Python designed to have fast performance, and with word embedding models built in, it’s perfect for a quick and easy start. I don't need to detail what spaCy does, it is perfectly summarized by spaCy in this article: **spaCy 101: Everything you need to know**.

Today, we will learn to use a pre-trained embedding to convert a text into a vector to compute similarity between words or sentences. Remember, embeddings translate large sparse vectors into a lower-dimensional space that preserves semantic relationships.
Word embeddings is a technique where individual words of a domain or language are represented as real-valued vectors in a lower dimensional space. The BoW representation's dimension depends on the size of the vocabulary. But it can easily reach 10k words. We will also learn to use NER and Part-of-speech. NER allows to identify and segment the named entities and classify or categorize them under various predefined classes. Part-of-speech is a special label assigned to each token (word) in a text corpus to indicate the part of speech and often also other grammatical categories such as tense, number (plural/singular), case etc.

## Exercises of the day

- Exercise 1 Embedding 1
- Exercise 2 Tokenization
- Exercise 3 Embeddings 2
- Exercise 4 Sentences' similarity 
- Exercise 5 NER
- Exercise 6 Part-of-speech tags

## Virtual Environment 
- Python 3.x
- Jupyter or JupyterLab
- Spacy

I suggest to use the most recent libraries.

## Ressources

- https://spacy.io/usage/spacy-101
- https://spacy.io/api/doc
- https://www.analyticsvidhya.com/blog/2021/06/nlp-application-named-entity-recognition-ner-in-python-with-spacy/
- https://medium.com/mlearning-ai/nlp-04-part-of-speech-tagging-in-spacy-dc3e239c2726