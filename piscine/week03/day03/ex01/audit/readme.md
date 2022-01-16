##### The question 1 is validated if the chunk of code is: 

```
model.compile(
  optimizer='adam',
  loss='mse',
  metrics=['mse'] 
)
```
All regression metrics or losses used are correct. As explained before, the loss functions are chosen thanks to nice mathematical properties. That is why most of the time the loss function used for regression is the MSE or MAE. 

https://keras.io/api/losses/regression_losses/
https://keras.io/api/metrics/regression_metrics/