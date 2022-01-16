##### The question 1 is validated if the code that creates the neural network is: 

```
model = keras.Sequential()
model.add(Dense(8, input_shape=(5,), activation= 'sigmoid'))
model.add(Dense(4, activation= 'sigmoid'))
model.add(Dense(1, activation= 'linear'))

```

The first two layers could use another activation function that sigmoid (eg: relu)