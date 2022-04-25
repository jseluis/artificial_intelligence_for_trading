
# Trading with Momentum

## Project Description: 

##### Here you will build your own deep learning model to classify the sentiment of messages from [StockTwits](https://stocktwits.com/), a social network for investors and traders. Your model will be able to predict if any particular message is positive or negative. From this, you'll be able to generate a signal of the public sentiment for various ticker symbols.


###### *Additional Resources*

Additional resources: If you would like to know some additional practical tips about how to improve your network and training, you may read this https://danijar.com/tips-for-training-recurrent-neural-networks/ and this https://towardsdatascience.com/stock-prediction-using-recurrent-neural-networks-c03637437578


###### *Important Notes*: 

## From the Market Data (*Important*)

- The function resample_prices computes the monthly prices.

- The resample prices method has been correctly implemented :+1:

- The function compute_log_returns computes the log returns from the prices.
:white_check_mark:

- The function shift_returns computes the shifted returns.

- shift_returns is perfectly implemented!

## Portfolio (*Important*)

- The function get_top_n selects the top_n number of the top performing stocks.

- get_top_n will correctly select the top_n number of the top performing stocks.

- You can implement get_top_n efficiently using iterrows in the foll manner:

- Create a dataframe with the same columns and indeices as prev_returns, but filled with 0s

- You can implement get_top_n most efficiently in the foll manner:

- return prev_returns.apply(lambda x: x >= pd.Series.nlargest(x, top_n).min(), axis=1).astype('int64')

- You can implement get_top_n in the foll manner:

- return (prev_returns.rank(axis=1, ascending=False)<=top_n).applymap(int)

- The function portfolio_returns calculates the projected returns. This formula works since the long and short positions can net out so in aggreagte since all stocks have equal waiting then the weighted average is the arithmetic return

- The projected returns are calculated correctly.

## Statistical Tests

- The function analyze_alpha calculates the t-value and p-value.

- tvalue and pvalue are correctly calculated. Good job dividing the pvalue by 2 :heavy_check_mark:
Here is some more information on t-statistic and p-value. Also this link shows us the differences between one-tailed & two-tailed tests and when to use each one.

- The p-value are calculated correctly.

- The analysis and reasoning given for what the pvalue indicates about the signal is apt. Its great to see that you have compared your p-value to alpha :+1: This link provides some more information on hypothesis testing.

   
   ```python
   largest = pd.DataFrame(0, index=prev_returns.index, columns=prev_returns.columns)

    # Iterate through the rows of prev_returns
    for index, _ in prev_returns.iterrows():
        # Create a list of the columns that contain the n largest values
        top_stocks = list(prev_returns.loc[index].nlargest(top_n).index.get_values())
        # Replace 0 values with 1 when a column contains one of the n largest values 
        largest.loc[index, top_stocks] = 1
    return largest 
    ```