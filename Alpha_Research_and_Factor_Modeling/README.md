
# Alpha Research and Factor Modeling

## Project Description: 

* Build a statistical risk model using PCA. You’ll use this model to build a portfolio along with 5 alpha factors. You’ll create these factors, then evaluate them using factor-weighted returns, quantile analysis, sharpe ratio, and turnover analysis. At the end of the project, you’ll optimize the portfolio using the risk model and factors using multiple optimization formulations. For the dataset, we'll be using the end of day from Quotemedia and sector data from Sharadar.


###### *Important Notes*: 

### (*Important*)

* For further reading

    https://www.investopedia.com/terms/m/multifactor-model.asp
    https://corporatefinanceinstitute.com/resources/knowledge/other/multi-factor-model/

## Statistical Risk Model (Steps)

* The function fit_pca fits the PCA model with returns.

  ![myImage](https://udacity-reviews-uploads.s3.us-west-2.amazonaws.com/_attachments/3354060/1635731882/FireShot_Capture_124_-_project_4_starter.ipynb_-_Colaboratory_-_colab.research.google.com.png)

* The function factor_betas gets the factor betas from the PCA model.

  ![myImage](https://udacity-reviews-uploads.s3.us-west-2.amazonaws.com/_attachments/3354060/1635731991/FireShot_Capture_125_-_project_4_starter.ipynb_-_Colaboratory_-_colab.research.google.com.png)

* The function factor_returns gets the factor returns from the PCA model.

  ![myImage](https://udacity-reviews-uploads.s3.us-west-2.amazonaws.com/_attachments/3354060/1635732039/FireShot_Capture_126_-_project_4_starter.ipynb_-_Colaboratory_-_colab.research.google.com.png)

* The function factor_cov_matrix gets the factor covariance matrix.

* The function idiosyncratic_var_matrix gets the idiosyncratic variance matrix.

* The function idiosyncratic_var_vector gets the idiosyncratic variance vector.

* The function predict_portfolio_risk gets the predicted portfolio risk.

## Create Alpha Factors

* The function mean_reversion_5day_sector_neutral generates the mean reversion 5 day sector neutral factor.

* The function mean_reversion_5day_sector_neutral_smoothed generates the mean reversion 5 day sector neutral smoothed factor.

## Evaluate Alpha Factors

* The function sharpe_ratio gets the sharpe ratio for each factor for the entire period. The smoothed factors have a lower sharpe ratio

![myImage](https://udacity-reviews-uploads.s3.us-west-2.amazonaws.com/_attachments/3354060/1635732245/FireShot_Capture_127_-_project_4_starter.ipynb_-_Colaboratory_-_colab.research.google.com.png)


* There is no expectation of any major improvement in the factor since the factor is already stable.

* The function OptimalHoldings._get_obj returns the correct objective function.

* The function OptimalHoldings._get_constraints returns the correct list of constraints.

* The function OptimalHoldingsRegualization._get_obj returns the correct objective function.
