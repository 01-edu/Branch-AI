# Financial strategies on the SP500


In this project we will apply machine to finance. You are a Quant Researcher and your goal is to create a financial strategy based on a signal outputted by a machine learning model that overperforms the SP500. 

https://en.wikipedia.org/wiki/S%26P_500

The Standard & Poors 500 Index is a collection of stocks intended to reflect the overall return characteristics of the stock market as a whole. The stocks that make up the S&P 500 are selected by market capitalization, liquidity, and industry. Companies to be included in the S&P are selected by the S&P 500 Index Committee, which consists of a group of analysts employed by Standard & Poor's.
The S&P 500 Index originally began in 1926 as the "composite index" comprised of only 90 stocks. According to historical records, the average annual return since its inception in 1926 through 2018 is approximately 10%–11%.The average annual return since adopting 500 stocks into the index in 1957 through 2018 is roughly 8%. 
As a Quant Researcher, you may be able to beat the SP500 one year. The real challenge though is to beat the SP500 consistently over decades. That's what all hedge funds in the world are trying to do. 


The project is divised in parts: 

- **Data processing and feature engineering**: Build a dataset: insightful features and the target
- **Machine Learning pipeline**: Train machine learning models on the dataset and select the best model. 
- **Strategy backtesting**: Generate a strategy from the Machine Learning model output and backtest the strategy. As a reminder, the idea here is to see what would have performed the strategy if you would have invested. 

# Deliverables

## Data processing and features engineering
- Split the data in train and test (choose the year)
- Your first priority is to build a dataset without leakage !!! NO LEAKAGE !!! 


We assume it is day D and we want to take a position on the next h days on the next day. The position starts on day D+1 (included). To decide wether we take a short or long position the return between day D+1 and D+2 is computed and used as a target. Finally, as features on day contain information until day D 11:59pm, target need to be shifted. As a result, the final dataframe schema is: 



| Index    |  Features                   |Target |
|----------|:-------------:              |------:|
| Day D-1  |  Features until D-1 23:59pm | return(D, D+1) |
| Day D    |  Features until D 23:59pm | return(D+1, D+2) |
| Day D+1  |  Features until D+1 23:59pm   | return(D+2, D+3) |
    

- CORRECTION: check que les features et returns sont calculés avec des groupby ... 


- Features:
    - Bollinger
    - RSI
    - MACD

- Target:
    - On day D, the target is: **sign(return(D+1, D+2))**

## Machine learning pipeline

- CV module:
    - plot (optional)
    - return folds
    - TEMPORAL

- Feature importance 

- The signal has to be generated following the chosen cross validation:
Train on 5y or 10y and predict on 1y
## Strategy backtesting

- Module backtest:
    - Sharpe 
    - Pnl 
    - Max draw down 
    - Turnover

The goal of this project is to create financial strategies on the SP500 based on Machine Learning signals. 

Stock picking  short the X top and bottom stocks 
Data: 

- Funda
- Market data
- Alternative data 


```
project
│   README.md
│   environment.yml    
│
└───data
│   │   train.csv
│   │   test.csv
│   │   xxx.csv
│
└───results
│   │   
|   |───model (free format)
│   │   │   my_own_model.pkl
│   │   │   my_own_model_architecture.txt
│   │   │   tensorboard.png 
│   │   │   learning_curves.png 
│   │   │   pre_trained_model.pkl (optional)
│   │   │   pre_trained_model_architecture.txt (optional)
│   │  
|   |───hack_cnn (free format)
│   │   │   hacked_image.png   (optional)
│   │   │   input_image.png
│   │   
|   |───preprocessing_test 
|   |   |   input_video.mp4  (free format)
│   │   │   image0.png  (free format)
│   │   │   image1.png
│   │   │   imagen.png
│   │   │   image20.png
|
|───scripts
│   │   train.py
│   │   predict.py
│   │   preprocess.py
│   │   predict_live_stream.py
│   │   hack_the_cnn.py




``` 