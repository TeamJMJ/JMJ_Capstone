# JMJ_Capstone
Cryptocurrency's growing acceptance and trading volume has led to increased analysis using historical data. Our team hypothesizes that Twitter activity influences crypto prices. We aim to predict buy/sell signals using Twitter sentiment, Google Trends, News API, and market trends with machine learning techniques.

## How to Run this Project
You can run each Jupyter notebook in order but here is a summary/instructions for each notebook:
1) STEP 1 Twitter Scrapper and Extracts
* We extract 3 years of Bitcoin Twitter data using snscrape
* You need to install the development version of snscrape. You can install with `pip install git+https://github.com/JustAnotherArchivist/snscrape.git`
2) STEP 2 Data Extract and Merging
* We extract and merge together Bitcoin financial data from the Binance API, News sentiment data from the Alpaca API, Google Trends data using Pytrends, and the Twitter data from Step 1
* You need to create a Binance and Alpaca accounts to obtain API keys for each respective API
* KNOWN ISSUE: The Pytrends API as of Mar 2023 will return a `TooManyRequestsError: The request failed: Google returned a response with code 429 error` if you try to run it normally. To workaround this error, you will have to set headers obtained from your web browser from the Google Trends website. The headers listed in this notebook may or may not work on your specific machine.
3) STEP 3.1 Model Analysis PyCaret All Features
* Run Pycaret on our merged data to quickly identify the top performing models at a glance
* Pycaret only run on Python 3.8 or below at the moment
4) STEPS 3.2 - 3.6 Training and Testing of Models on ALL Features
* Trained and tested the top-performing models identified by Pycaret on ALL Features as well as putting those models in both an Ensemble and Stacking Models and a LSTM deep learning model
5) STEP 4.1 Model Analysis PyCaret Priority Features Assessment
* Identify the Priority Features from the merged data for each model using Pycaret
6) STEPS 4.2 - 4.7 Training and Testing of Models on Priority Features
* Train and test all the models on the top 87 Features identified by Pycaret
7) STEP 5 Back Testing
* We take all the predictions from the different models and compare them to the base model (benchmark) investment strategy of buying and holding Bitcoin worth 100K USD
8) STEP 6 Trading Bot
* Created a sample trading bot 
* We take our top performing model (Stacking_LR_model_JT2019to2022TEST_news_google), and then use it to create buy and sell signals(prediction) for us to invest on
