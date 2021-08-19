# NFLX_TSLA_Analysis
### Analysis of NFLX and TSLA stocks


- This Analysis was undertaken in order to compare the fluctuating stock prices of two technology based companies - Tesla (TSLA) and Netflix (NFLX) for a year period starting in May of 2020 and ending in May of 2021.  These companies, along with many other companies that would be considered technology companies (Apple, Google, Nvidia etc) have seen their sky rocketing valuations stand out, even in a market that on the whole, is currently experiencing a prolonged period of growth across all sectors.  

- To better understand the underpinning ascension of these two companies, I used the Pandas DataReader libary to examine finanical data from Yahoo Finance using their APIs.  From here, I expanded on the available data by creating new columns for finanical analysis tools such as Moving Average Convergence Divergence (MACD) idicators, Simple Moving Averages (sMA), Expoential Moving Averages (EMA), Stochastic Oscillators among others.  Utilizing those tools, I was able to exmaine in more depth analysis on exactly how those stocks performed and how solid the numbers behind those performances were. 

- After loading in the data for both stocks utilizing the Pandas Data Reader to make an API call to Yahoo Finance, the first thing I wanted to explore involved creating moving averages.  Firstly, to create the simple moving averages (SMA), I used the following code to create a new column in the DataFrame:``` df["MA_10"]=df["Close"].rolling(10).mean() ``` This created a simple 10 day rolling average of the the closing values throughout the entire timeframe.  Then, to create the exponential moving average (EMA), which is more predictive than a SMA because it weights the most recent values heavier, I used the following code to create an additional column: ```df["EMA_10"]= df["Close"].ewm(span=10, adjust=False).mean() ``` for the EMA of both stocks.  Then, in order to visualize those moving averages, I made a line graph of the SMA and EMA with the share price as an overlay.  Below is the outocme for both TSLA and NFLX

![ALT_TEXT](https://github.com/Nickguild1993/NFLX_TSLA_Analysis/blob/main/Visuals/TSLA_EMA_MA.png)

![ALT_TEXT](https://github.com/Nickguild1993/NFLX_TSLA_Analysis/blob/main/Visuals/NFLX_EMA_MA.png)

- In both cases, the exponential moving average tracked future share prices better than the simple moving average, and was much more reactive to incoming corrections.





- VOLATILITY 

![ALT_TEXT](https://github.com/Nickguild1993/NFLX_TSLA_Analysis/blob/main/Visuals/TSLA_Volatility_Hist.png)

![ALT_TEXT](https://github.com/Nickguild1993/NFLX_TSLA_Analysis/blob/main/Visuals/NFLX_Volatility.png)
