# Smart Beta and Portfolio Optimization

## Project Description: 

##### Build a smart beta portfolio and compare it to a benchmark index. To find out how well the smart beta portfolio did, you’ll calculate the tracking error against the index. You’ll then build a portfolio by using quadratic programming to optimize the weights. Your code will rebalance this portfolio and calculate turn over to evaluate the performance. You’ll use this metric to find the optimal rebalancing Frequency. For the dataset, we'll be using the end of day from Quotemedia.

###### *Important Notes*: 

## Smart Beta Portfolio (Steps)

* The function generate_dollar_volume_weights computes dollar volume weights.

- Calculate the dollar volume to generate dollar volume weights in the generate_dollar_volume_weights function. Normalization of values is done correctly for the sum of the total dollar-volume of the stocks traded every day. :thumbsup:.

* An alternative way to implement generate_dollar_volume_weights is as following:

```py
return (close*volume).apply(lambda x: x/x.sum(),axis=1)
```

* This article explains a few index weighting strategies other than Market-Cap weighted indexes.
https://www.ftserussell.com/education-center/how-are-indexes-weighted

* The function calculate_dividend_weights computes dividend weights. Implemented the calculate_dividend_weights function by calculating the total dividend yield over time. :ok_hand:

* An alternative way to implement calculate_dividend_weights is as following:

```py
return dividends.cumsum().apply(lambda x:x/x.sum(),axis=1)
```

* This article provides a good explanation of Portfolio Weights.
https://www.cfajournal.org/investments-portfolio-weights/

* The function generate_returns computes returns. Implemented the generate_returns function to generate returns data for all the stocks and dates from price data. You would have noticed that we're implementing returns and not log returns because we're not dealing with volatility, hence we don't have to use log returns. :thumbsup:

* An alternative way to compute returns is as follows: 

```py
return (prices / prices.shift(1)) - 1
```

* Here is a document that explains different aspects of portfolio return in detail.
https://www.cpaireland.ie/CPAIreland/media/Education-Training/Study%20Support%20Resources/2019%20Articles/P1MFRiskReturn.pdf

* The function generate_weighted_returns computes weighted returns. You will implemented the generate_weighted_returns function correctly to generate weighted returns using the simple multiplication of returns and weights. :ok_hand:

* The function calculate_cumulative_returns computes cumulative returns. You have implemented the calculate_cumulative_returns correctly to calculate the cumulative returns over time given the returns. We can use the cumulative returns to compare the performance between the ETF and index. :clap:

* The function tracking_error computes tracking error.

* You have correctly implemented the tracking_error function to return the tracking error between the ETF and benchmark. Your Smart Beta Portfolio is complete now, we are now ready for Portfolio optimization from the next cell. :thumbsup:

## Portfolio Optimization

* The function get_covariance_returns computes covariance of the returns. You have implemented the get_covariance_returns to calculate the covariance of the returns which can be used to calculate the portfolio variance. :ok_hand:

* An alternative way to implement get_covariance_returns is as following:

```py
return np.cov(returns.T.fillna(0))
```

* The function get_optimal_weights computes optimal weights. You have optimized the weights using cvxpy to implement the get_optimal_weights function. Variable, Objective and Constraints are set properly to solve the optimization problem with the help of cvx.Problem(objective, constraints).solve(). You have also returned x.value correctly in the end. :clap:

* The function rebalance_portfolio computes weights for each rebalancing of the portfolio. You will ebalance the portfolio over the same period instead of using the same weights for the entire history. You have rebalanced the portfolio every n number of days, using shift_size. When rebalancing, you also looked back at a certain number of days of data in the past, denoted as chunk_size. You have also computed the optimal weights using get_optimal_weights and get_covariance_returns functions. :ok_hand:.

* The function get_portfolio_turnover computes cost of all the rebalancing. Here you will implement Smart Beta Portfolio which is evident by the impressive portfolio turnover value of 16.72683266050277 you have achieved from your portfolio. However, we need to be cognizant that this is a simulated market cap weighted index with large dollar volume stocks only which is not comparable one on one with the real world portfolios.