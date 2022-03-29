##### The question 1 is validated if the code that creates the neural network is: 

```
model = keras.Sequential()
model.add(Dense(16, input_shape=(5,), activation= 'sigmoid'))
model.add(Dense(8, activation= 'sigmoid'))
model.add(Dense(5, activation= 'softmax'))
```