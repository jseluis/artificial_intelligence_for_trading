
# Breakout Strategy

## Project Description: 

##### Implement the breakout strategy, find and remove any outliers, test to see if it has the potential to be profitable using a Histogram and P-Value using a dataset with the end of day from Quotemedia.


###### *Important Notes*: 

##  Generate Signal (*Important*)

* The function get_high_lows_lookback computes the maximum and minimum of the closing prices over a window of days.

* A breakout strategy seeks to benefit from the idea that stock prices typically oscillate within a range, so that when they begin to break out of the range, they are likely to continue breaking out. This function computes the range of the stock prices. If the stocks break out of the range then we can trade the stocks.

```python
close = df.reset_index().pivot(index='date', columns='ticker', values='adj_close')
high = df.reset_index().pivot(index='date', columns='ticker', values='adj_high')
low = df.reset_index().pivot(index='date', columns='ticker', values='adj_low')
```

[Check out OHLC lesson](https://www.youtube.com/watch?v=FgNY4YgVWFk)

Closing price is the end of day stock price.
Open price is the start of the day stocks price.
High price is the highest price of the stock over the entire day.
Low price is the lowest price of the stock over the entire day.

The function get_long_short computes long and short signals using a breakout strategy.

In this function, breakout strategy is actually implemented. When the stock price is out of the window, we can buy/sell the stocks accordingly.

The function filter_signals filters out repeated long or short signals.

Having additional signals to sell/buy the stocks are not helpful therefore we filter out these repeated long or short signals.

The function get_lookahead_prices gets the close price days ahead in time.

The function get_return_lookahead generates the log price return between the closing price and the lookahead price.

Raw return is defined as R = (p(t+1) - p(t)) / p(t), we can change to log return as follows;

R = p(t+1) / p(t) - p(t) / p(t)
R = p(t+1) / p(t) - 1

Taking logs on both sides;

lnR = ln(p(t+1) / p(t)) - ln(1)
lnR = ln(p(t+1) / p(t)) where ln(1) = 0
lnR = ln(p(t+1)) - ln(p(t)) using logarthmic rule

The function get_signal_return generates the signal returns.
Evaluate Signal

Correctly answers the question “What do the histograms tell you about the signal returns?"

To answer this question think about the following:

    Are the histograms skewed, if yes which side?
    Is it because of outliers, what could be the reason?
    Which side do the outliers appear and what does it signify?
    What will happen to the distribution of the histograms if the outliers are removed?

Another way to visually check if a distribution is normal is or not, is to create a QQ (quantile-quantile) plot. See this link for how to use QQ plots.

That's correct! There's a skew in the distribution. It is actually because of the outliers. The signal returns distribution can be used to identify any outliers in the distribution. Here's the lesson video that talks about identifying the outliers in the histogram of the signal returns https://www.youtube.com/watch?v=BSLGZz0RzTg
Outliers

The function calculate_kstest calculates the ks and p values.

Nice job in first getting the normal_args (mean and standard deviation) of the entire portfolio and then running the KS test on a normal distribution against each stock's signal returns with normal_args of the entire portfolio.

The function find_outliers returns the list of outlying symbols.

Both the conditions to find the outliers are satisfied;

Symbols that pass the null hypothesis with a p-value less than pvalue_threshold.
Symbols that with a KS value above ks_threshold.

