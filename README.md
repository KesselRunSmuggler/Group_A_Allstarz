# Group_A_Allstarz
## ALLSTARZ INTRO

**Viseth Auk**

**Toby Martin**

**Simon Zhang**

**Luke Macumber**

The Question is:  Can we utilise ML to accurately predict entry and exits signals whilst trading, in order to make a consistent profit?

LSTM vs SMA vs Buy & HODL

Compare and contrast buy & HODL, MA trading and LSTM (close price)

# LSTM Model and Its Application in the Financial Markets 
<div style="width:1280px">

In many research publications there has been a lot of discussions around a new trading phenomenon used in various trading strategies known as the LSTM Model, often referred to as the Long-Term Short-Term Memory Model which is used in the neural network or machine learning arena. We would like to uncover the truth behind this style of trading, is it truth or fiction?

<br/>In previous works we have seen much of the hype surrounding neural networks and its applications more focused in image-based applications such as fingerprint recognition, facial recognition, etc.
However, models in **Recurrent Neural Networks** (RNNs) have been successfully used in recent years to predict future events in time series as well. RNNs have contributed to breakthroughs in a wide variety of fields centered around predicting sequences of events. The reason they work so well is because LSTM is able to store past information that is important, and forget the information that is not. 
    
<br/> LSTM has three gates:
- The **Input Gate**: The input gate adds information to the cell state
- The **Forget Gate**: It removes the information that is no longer required by the model
- The **Output Gate**: Output Gate at LSTM selects the information to be shown as output

<br> The diagram below illustrates the gate setup:<br/>
![GATES](./images/gates.png "LSTM GATES")

    

<br/>In this project, we will explore and demonstrate how one type of RNN model, the **Long Short-Term Memory (LSTM)** network, can be used to predict price movement in financial time series data which is considered to be perhaps the most chaotic and difficult of all time series. We will also seek to use technical indicators such as the Moving Average and the MACD with LSTM to try and predict price movements and profit from it in our strategy.

</div>

# Definitions

Before we dive into it let's understand some terminologies commonly used in the model

- **Features**  : The feature / object we gonna use to predict the next price value.
- **Dropout**   : The dropout rate is the probability of not training a given node in a layer.This helps the model to not overfit our training data.
        
- **Optimiser** : Optimisation algorithm to use (defaults to Adam).
- **Batch Size**: The number of data samples to use on each training iteration.
- **Epoch**     : The number of times that the learning algorithm will pass through the entire training dataset
- **HODL**     : Hold On For Dear Life

# Data Exploration

<div style="width:1280px">

The data we will be working with will be daily data of cryptocurrencies. We will be focusing on the prices of BTC, if we have time
we could look at other cryptocurrencies. Our intention is to see if LSTM can be used to predict market price changes and if it is 
possible to incorporate this model to profit from in our trading strategies. The data is taken from **coinmarketcap.com** and extracted into a CSV file

</div>

# Data Visualisation

<div style="width:1280px">

We need to inspect and see what sort of data we have we expect to see data with various patterns occurring overtime
to ensure that the data can account for different changes in market behaviour over the period. This ensure consistency and trust 
that the data have enough coverage for the forever changing market conditions.

</div>


# Our Moving Average Strategy ( **Customised** )

<div style="width:1280px">

Comparison 1: We will conduct a long only moving average strategy. Our strategy is as follows:

- We will use the two-day rule only that is to say that we start the trade only after it is confirmed by one more day’s closing price, and keep the date as the entry point only if the 20 days MA is above 50 days MA two days in a row. **This approach will help us to avoid daily trading noise fluctuations**. When this happens, we will have the entry points in the column firstbuy where the value equals to True.<br/><br/>

- At the buy entry we will purchase '50' units of the specified asset (bitcoin)<br/><br/>

- We hold the position for 20 days and sell at the 20 days close price from the purchase date
<br/><br/>



# Moving Average Back Test Results
<div style="width:1280px">
To determine how well we performed in our moving average strategy, we can print out the long position profit list and calculate the sum.


<br/>![](./images/MA_vs_CumProfit.png) <br/>

<br/>![](./images/ma_results.png)<br/>

# Buy & Hold Strategy
<div style="width:1280px">
To buy and hold simply means buy on the first day and sell on the last day. In this case, we will be buying 50 units of bitcoin and then selling 50 units at the close price of the last day on the timeseries.
</div>

### BUY & HOLD STRATEGY RETURN:
===============================================

Initial cost of purchasing 50 BTC: $5085.00

Income from selling 50 BTC on the last day: $1687300.12

profit = $1682215.12

buy & hold return = 33081.91%

===============================================

# Steps Undertaken to build LSTM model:



## Define the Features
The feature column we want to use to predict is the closing price.<br/>
Our LSTM trading strategy are as follows: <br/>
buy if: (actual / predicted) < 1 – threshold (2%)<br/>
close position if: (actual / predicted) > 1 + threshold (2%)

## Split the Data for Training Sets


## Scale the Data
We scale the data so it is uniform and comparable

## Re-Shape the Data

## Build the LSTM Model

## Train the Data

## Evaluate the model

<br> The chart below compares the Actual vs Predicted Prices for the LSTM model:<br/>
![](./images/lstm_actual_vs_predicted.png)<br/>

![](./images/lstm_results.png)


# Our Conclusion:

- Over the history of Bitcoin, the buy and hold strategy still wins out when compared to our MA strategy and the LSTM model.
- LSTM is very difficult to configure to get the best results as it relies on so many parameters and we would need to understand and test each parameter thoroughly. Furthermore, there are still randomness in our results and we are unable to compare due to the fact the same parameters are not always reproduceable. This is because the LSTM model drops random data points as it is executed. 
- With more time and honing of the parameters, we believe that it could be possible to out perform other investments using the LSTM model. However, when it comes to Bitcoin, the price appreciation year-on-year would be hard to beat.
