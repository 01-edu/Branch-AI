##### The exercice is validated is all questions of the exercice are validated

##### The question 1 is validated if the output of the first ten values of the train labels are: 

```
array([[0, 1, 0],
       [0, 0, 1],
       [0, 1, 0],
       [0, 0, 1],
       [0, 0, 1],
       [1, 0, 0],
       [0, 1, 0],
       [1, 0, 0],
       [0, 1, 0],
       [0, 0, 1]])
```

##### The question 2 is validated if the accuracy on the test set is bigger than 90%. To evaluate the accuracy on the test set you can use: `model.evaluate(X_test_sc, y_test_multi_class)`.

Here is an implementation that gives 96% accuracy on the test set. 

```
model = Sequential()
model.add(Dense(10, input_dim=4, activation='sigmoid'))
model.add(Dense(3, activation='softmax'))
# Compile model
model.compile(loss='categorical_crossentropy', optimizer='adam', metrics=['accuracy'])
model.fit(X_train_sc, y_train_multi_class, epochs = 1000, batch_size=20)
```