# Credit scoring

## Machine learning model

- the model is trained only the training set 
- the AUC on the test set is higher than 75% 
- the model learning curves should prove that the model is not overfitting 
- the training has been stopped early enough to avoid the overfitting
- the text document should describe the methodology used to train the machine learning model.
- predict.py runs without any error and returns: 


    ```prompt 
    python predict.py

    AUC on test set: 0.76

    ```

This article gives a complete example of a good modelling approach: 

https://medium.com/thecyphy/home-credit-default-risk-part-2-84b58c1ab9d5


## Model's interpretability

- Feature importance:
    - the importance of all features used by the model are computed and showed in a visualisation. You should be careful here to associate the right variables to the their feature importance. Sometimes, the preprocessing pipeline can remove some features during the features selection step for instance. 


- Descriptive variables: 
These are important to understand for example the age of the client. If the data could be scaled or modified in the preprocessing pipeline but the data visualised here should be "raw". This part is validated if the visualisations are computed for the 3 clients.
    - visualisations that show at least 10 variables describing the client and its loan(s)
    - visualisations that show the comparison between this client and other clients.

- SHAP values on the model:
    - a summary plot shows the important features and their impact on the target. This is optional if you have already computed the features importance. 

- SHAP values on predictions:
This part is validated if the SHAP visualisations are computed for the 3 clients.
    - a force plot shows what variables contributes the most to the score. 
    - **check that the score outputted by the force plot corresponds to the one outputted by the model.** 



