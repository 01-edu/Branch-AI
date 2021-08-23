# Financial strategies on the SP500
 
 This documents is the correction of the project 4. Some steps are detailed in W1D5E4. 
 
## **Data processing and feature engineering**

- Split train/test: this step is validated if you 
- No leakage: unfortunately there's no autamated way to check if the dataset is leaked. This step is valiated if the features of date d are built as follow: 

| Index    |  Features                   |Target |
|----------|:-------------:              |------:|
| Day D-1  |  Features until D-1 23:59pm | return(D, D+1) |
| Day D    |  Features until D 23:59pm | return(D+1, D+2) |
| Day D+1  |  Features until D+1 23:59pm   | return(D+2, D+3) |

- Features: some of the features as the MACD are computed on a rolling fashion. This step is validated if you grouped the features by ticker before to compute the features. 

- Target: This step is validated if you grouped the prices by ticker before to compute the returns. 



## **Machine Learning pipeline**

### cross-validation

- This step is validated if:
    - there are at least 10 folds in total ( train + test set)
    - all train folds have more than 2y history. If you use time series split, checking that the first fold has more than 2y history is enough. 
    - the last validation set of the train set doesn't overlap on the test set. 
    - none of the folds contain data from the same day. The split should be done on the dates. 
    - there's a plot showing your cross-validation. As usual, all plots should have named axis and a title.If you chose a Time Series Split the plot should look like this: 


![alt text][timeseries]

[timeseries]: images/Time_series_split.png "Time Series split" 


### model selection

- This step is validated if:
    -  the test set is not used
    - the selected model is saved in the pkl file and described in a txt file

### selected model

- This step is validated if:
    - the ml metrics computed on the train set are agregated: sum or median. 
    - the ml metrics are saved in a csv file.
    - metric_train.png shows a plot similar to the one below
    - the top 10 important feature per fold are in `top_10_feature_importance.csv`. 

Note that, this can be done also on the test set **IF** this hasn't helped to select the pipeline. 

![alt text][barplot]

[barplot]: images/metric_plot.png "Metric plot"

### machine learning signal

- This step is validated if: 
    - **The pipeline shouldn't be trained once and predict on all data points !** 
    - as explained: The signal has to be generated with the chosen cross validation: train the model on the train set of the first fold, then predict on its validation set; train the model on the train set of the second fold, then predict on its validation set, etc ... Then, concatenate the predictions on the validation sets to build the machine learning signal.


## **Strategy backtesting**

### convert machine learning signal into a strategy
- This step is validated if: 
    - the transformed machine learning signal (long only, long short, binary, ternary, stock picking, proportional to probability or custom ) is multiplied by the return between d+1 and d+2. As a reminder, the signal at date d predicts wether the return between d+1 and d+2 is increasing or deacreasing. Then, the PnL of date d could be associated with date d, d+1 or d+2. This is arbitrary and should impact the value of the PnL. 
    - invest the same amount of money every day. One exception: if you invest 1$ per day per stock the amount invested every day may change depending on the strategy chosen. If you take into account the different values of capital invested every day in the calculation of the PnL, the step is still validated. 

### metrics and plot
- This step is validated if: 
    - the Pnl is computed as: strategy * futur_return. And strategy gives the amount invested at time t on asset i. 
    - the plot `strategy.png` contains:
        - x axis: date
        - y axis1: PnL of the strategy at time t
        - y axis2: PnL of the SP500 at time t
        - Use the same scale for y axis1 and y axis2
        - a line that shows the separation between train set and test set 

### report
- This step is validated if: 
    - `report.md`details :
    - the features used
    - the pipeline used
        - imputer
        - scaler
        - dimension reduction
        - model
    - the cross-validation used
        - length of train sets and validation sets
        - cross-validation plot (optional)
    - strategy chosen
        - description
        - PnL plot
        - strategy metrics on the train set and test set
