# NLP-enriched News Intelligence platform

This is the correction of the project 2: **NLP-enriched News Intelligence platform**.

## Deliverables

```
project
│   README.md
│   environment.yml    
│
└───data
│   │   topic_classification_data.csv
│   
└───results
│   │   topic_classifier.pkl
│   │   learning_curves.png
|
|───nlp_engine
│   

```

## Validation

The project is validated if:

### Scrapper

- There are at least 300 news articles stored in the file system or the database.
- Run the scrapper and fetch 3 documents. The scrapper is not expected to fetch n documents, you can stop it manually.

### NLP engine

- Run the nlp_engine on the 3 documents you fetched.

### Topic classfier

- The **accuracy** on the test set is bigger then **95%**.
