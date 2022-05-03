##### The question is validated if the scores outputted are close to the scores below. Some of the algorithms use random steps (random sampling used by the `RandomForest`). I used `random_state = 43` for the Random Forest, the Decision Tree and the Gradient Boosting. 

```console
# Linear regression 

TRAIN
r2 on the train set:  0.34823544284172625
MAE on the train set:  0.533092001261455
MSE on the train set:  0.5273648371379568

TEST
r2 on the test set:  0.3551785428138914
MAE on the test set:  0.5196420310323713
MSE on the test set:  0.49761195027083804


# SVM 

TRAIN
r2 on the train set:  0.6462366150965996
MAE on the train set:  0.38356451633259875
MSE on the train set:  0.33464478671339165

TEST
r2 on the test set:  0.6162644671183826
MAE on the test set:  0.3897680598426786
MSE on the test set:  0.3477101776543003


# Decision Tree

TRAIN
r2 on the train set:  0.9999999999999488
MAE on the train set:  1.3685733933909677e-08
MSE on the train set:  6.842866883530944e-14

TEST
r2 on the test set:  0.6263651902480918
MAE on the test set:  0.4383758696244002
MSE on the test set:  0.4727017198871596


# Random Forest

TRAIN
r2 on the train set:  0.9705418471542886
MAE on the train set:  0.11983836612191189
MSE on the train set:  0.034538356420577995

TEST
r2 on the test set:  0.7504673649554309
MAE on the test set:  0.31889891600404635
MSE on the test set:  0.24096164834441108


# Gradient Boosting

TRAIN
r2 on the train set:  0.7395782392433273
MAE on the train set:  0.35656543036682264
MSE on the train set:  0.26167490389525294

TEST
r2 on the test set:  0.7157456298013534
MAE on the test set:  0.36455447680396397
MSE on the test set:  0.27058170064218096

```

It is important to notice that the Decision Tree overfits very easily. It learns easily the training data but is not able to extrapolate on the test set. This algorithm is not used a lot because of its overfitting ability.

However, Random Forest and Gradient Boosting propose a solid approach to correct the overfitting (in that case the parameters `max_depth` is set to None that is why the Random Forest overfits the data). These two algorithms are used intensively in Machine Learning Projects.
