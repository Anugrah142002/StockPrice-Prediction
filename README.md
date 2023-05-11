# Introduction
Stock price forecasting is an important and thriving topic in financial engineering especially since new techniques and approaches on this matter are gaining ground constantly. In this project, we make use of Sentiment Analysis on a set of tweets targeted at a particular company(HDFC in our case) over a period of 9 days to forecast how the market will behave in the future. The score of the sentiment analysis is then used as one of the input features for our neural network which then uses the training set along with the stock price data(obtained using the Yfinance library) for each day to get the optimum set of weights. This final regression function is then used for the prediction of future stock prices.

The tweet data is taken over a period of 9 days only because of the restrictions of the Twitter API, however in order to make a more accurate prediction (keeping in mind to avoid overfitting) a larger training set would be recommended.


# Dataset
To obtain the required Tweets, we first applied for Twitter Developer Access. Then, with the keys provided, we set up our Twitter API. We created an authentication object and an API object. After authenticating credentials, we were ready to extract the required data.

We imported the tweepy library to access the required data. We used the Cursor object and the api.search function to extract tweets which contain a specific hashtag (in our case: #ITC). We extracted the tweets as well as the timestamps at which they were created.

The daily stock prices of the company(historical data) were obtained using the yfinance library for the same time period over which the tweets were collected. The company was selected by specifying the ticker(hdfcbank.ns in our case).

Also in order to visualize the data in a better way in the form of dataframes, we made use of the pandas and numpy libraries.

# Stock data preprocessing
Stock data from the yahoo finance(throughAPI) provided us with certain heads of a stock. We further required HLPCT (stands for ”High-Low Percentage”) and PCTchange (stands for ”Percentage change”) heads as inputs for our model along with Adj CLOSE, VOLUME.

    Formulae used:                  HLPCT = (High-Low)/High
                                      PCTchange = (Close-Open)/Open

Another concern was of stock data for the days when markets were closed like weekends and holidays. So we went for an average value (of each head) of a previous day and the next day and used that as our data for the missing day. Also we used Adjusted Close values instead of normal closing values of stock prices as they provide a better insight into the stock’s current status after new company offerings etc.

# Twitter API and Data Preprocessing
To preprocess the relevant data in order to make it suitable for sentiment analysis, we removed mentions, hashtags, hyperlinks and ‘RT’ separately using the re library (re.sub() function to be exact) to replace redundant characters . All this was enclosed in a CleanTxt() function that we defined.

We also created a word cloud using the WordCloud library to get a visual representation of the most frequently used words in the relevant tweets. This helped better understand what the relevant words of the sentiment analysis were.

![image](https://github.com/Anugrah142002/StockPrice-Prediction/assets/96532336/fd50a871-459e-4153-b89f-2f41a98a4a50)
