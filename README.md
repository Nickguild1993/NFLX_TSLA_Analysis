# NFLX_TSLA_Analysis
### Analysis of NFLX and TSLA stocks


- This Analysis was undertaken in order to compare the fluctuating stock prices of two technology based companies - Tesla (TSLA) and Netflix (NFLX) for a year period starting in May of 2020 and ending in May of 2021.  These companies, along with many other companies that would be considered technology companies (Apple, Google, Nvidia etc) have seen their sky rocketing valuations stand out, even in a market that on the whole, is currently experiencing a prolonged period of growth across all sectors.  

- To better understand the underpinning ascension of these two companies, I used the Pandas DataReader libary to examine finanical data from Yahoo Finance using their APIs.  From here, I expanded on the available data by creating new columns for finanical analysis tools such as Moving Average Convergence Divergence (MACD) idicators, Simple Moving Averages (sMA), Expoential Moving Averages (EMA), Stochastic Oscillators among others.  Utilizing those tools, I was able to exmaine in more depth analysis on exactly how those stocks performed and how solid the numbers behind those performances were. 

- After loading in the data for both stocks utilizing the Pandas Data Reader to make an API call to Yahoo Finance, the first thing I wanted to explore involved creating moving averages.  Firstly, to create the simple moving averages (SMA), I used the following code to create a new column in the DataFrame:``` df["MA_10"]=df["Close"].rolling(10).mean() ``` This created a simple 10 day rolling average of the the closing values throughout the entire timeframe.  Then, to create the exponential moving average (EMA), which is more predictive than a SMA because it weights the most recent values heavier, I used the following code to create an additional column: ```df["EMA_10"]= df["Close"].ewm(span=10, adjust=False).mean() ``` for the EMA of both stocks.  Then, in order to visualize those moving averages, I made a line graph of the SMA and EMA with the share price as an overlay.  Below is the outocme for both TSLA and NFLX

![ALT_TEXT](https://github.com/Nickguild1993/NFLX_TSLA_Analysis/blob/main/Visuals/TSLA_EMA_MA.png)

![ALT_TEXT](https://github.com/Nickguild1993/NFLX_TSLA_Analysis/blob/main/Visuals/NFLX_EMA_MA.png)

- In both cases, the exponential moving average tracked future share prices better than the simple moving average, and was much more reactive to incoming corrections.


- Next, I wanted to examine the volatility- which can be thought of as how much variance in the share price a stock exhibits over a period of time.  Volatility isn't inherently good or bad, but what it does tell you is how much fluctuation a stock experiences.  Stocks that experience a high amount of volatility are considered to be riskier investments than those that experience less. However, the risk can lead to great returns, but it can also lead to losses.  Two important facets to consider when looking at a particular stock's volatility are what your personal risk tolarance is and what is causing the volatility.  Stocks are representative of their companies, so understanding what factors make a company volatile can lead to a greater understanding of why it's stock experiences it's level of volatility. 

- There are different ways to examine a stocks volatility as a percentage, the method I chose was using the standard deviation (std) of the log returns of the stocks. Below is the code that was used to get the measurments.

``` 
    df["Log_Returns"] = np.log(df["close"]/df["close"].shift())
     df["Log_Returns"].std()
     
     volatility = df["Log_Returns"].std()*252**.5
     str_vol = str(round(volatility, 5)*100)
    print("The volatility is :", str_vol)
```     
- The histrograms below representation of each stock's volatility percentage is below- with TSLA first followed by NFLX.


![ALT_TEXT](https://github.com/Nickguild1993/NFLX_TSLA_Analysis/blob/main/Visuals/TSLA_Volatility_Hist.png)

![ALT_TEXT](https://github.com/Nickguild1993/NFLX_TSLA_Analysis/blob/main/Visuals/NFLX_Volatility.png)

- What is clear is that both stocks experienced a tremendous amount of volatility from May of 2020 -> May of 2021.  While the volatility present in each led to very high levels of growth, it also lent itself to days of sharp correction in which the value of each stock would see preciptious falls.  Another thing to notice is where on the log return (X-Axis) the highest frequency took place.  For NFLX, the volatility was more in line with the mean share price throughout the timeframe, which did make it experience fewer days of losses, but also meant that the days in which its value increased were not of the same magnitude of TSLA's.  This comparision highlights the importance of gauging one's risk tolarance when buying equities- if you're comforable with wider value swings, then an equity with more volatility might make sense, but if you prefer more security, knowing that such security A) isn't guarunteed B) that the lower level of volatility does put a governor on returns, but also makes the investment less risky.
