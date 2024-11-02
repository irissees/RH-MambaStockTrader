# RH-MambaStockTrader
## Stock trading bot that integrates MambaSSM with Robinhood. 

This is a Python notebook that implements the [MambaStock source code](https://arxiv.org/abs/2402.18959) along with the RobinStocks module in order to trade stocks with artificial intelligence signaling. Mamba selective state modeling is a great trade off to the more popular Transfmormer model for time series forcasting because it is accurate and not nearly as computationally expensive.

This project uses daily OHLC stock data to forcasts the next day's close price. 
It also uses 100 day linear regression as a feature in order to increase the accuracy of predictions. 


#### Getting new data:
To get up to date data, you must have a Nasdaq Data Link API and be subscribed to the Sharadar Core US Equities Bundle. This costs around 80$ a month so running this bot is not free. You must also be logged into Robinhood to get the most current data if the market is still open. 

## Strategy:
The bot looks for crossovers using the actual price, predicted price and 100 day linear regression. 
### Buying:
The price must first be below the linear regression line before buying.
Since being below the linear regression line typically indicates a downtrend, the bot waits for the actual price to cross above the prediction price for an indicator of reversal. This means the price is moving faster than the bot is predicting and indicates the bearish trend fizzling out.
On certain stocks this doesn't signify much, but on bullish growth stocks such as FANNG they tend to vaccuum back towards the 100 day linear regression line and above.

### Selling:
The price must first be above the linear regression line before selling.
Since being above the linear regression line indicates an uptrend, the bot waits for the actual price to cross below the prediction price for an indicator of reversal. This means the price is moving faster than the bot is predicting and indicates the bullish trend fizzling out.

## Required: 
PyTorch with CUDA enabled
