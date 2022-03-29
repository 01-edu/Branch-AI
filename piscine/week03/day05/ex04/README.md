# Exercise 4 Sentences' similarity 

The goal of this exerice is to learn to compute the similarity between two sentences. As explained in the documentation: **The word embedding of a full sentence is simply the average over all different words**. This is how `similarity` works in SpaCy. This small use case is very interesting because if we build a corpus of sentences that express an intention as **buy shoes**, then we can detect this intention and use it to propose shoes advertisement for customers. The language model used in this exercise is `en_core_web_sm`.


1. Compute the similarities (3 in total) between these sentences:

    ```
    sentence_1 = "I want to buy shoes"
    sentence_2 = "I would love to purchase running shoes"
    sentence_3 = "I am in my room"

    ```