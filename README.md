# Introduction
Stock price forecasting is an important and thriving topic in financial engineering especially since new techniques and approaches on this matter are gaining ground constantly. In this project, we make use of Sentiment Analysis on a set of tweets targeted at a particular company(HDFC in our case) over a period of 9 days to forecast how the market will behave in the future. The score of the sentiment analysis is then used as one of the input features for our neural network which then uses the training set along with the stock price data(obtained using the Yfinance library) for each day to get the optimum set of weights. This final regression function is then used for the prediction of future stock prices.

The tweet data is taken over a period of 9 days only because of the restrictions of the Twitter API, however in order to make a more accurate prediction (keeping in mind to avoid overfitting) a larger training set would be recommended.

