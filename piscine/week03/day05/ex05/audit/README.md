##### The exercice is validated is all questions of the exercice are validated

##### The question 1 is validated if the ouptut of the NER is

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
##### The question 2 is validated if the output shows that the first occurence of apple is not a named entity. In my case here is what the NER returns: 

    ```
    Paul 1 5 PERSON
    Apple 50 55 ORG

    ```