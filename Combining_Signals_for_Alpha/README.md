Combining Signals for Enhanced Alpha

## Project Description: 

##### Combine signals on a random forest for enhanced alpha, and solve the problem of overlapping samples. For the dataset, we'll be using the end of day from Quotemedia and sector data from Sharadar.

###### *Additional Resources*

# Features and Labels

* Describe the relationship between the shifted labels.

* There's a high relationship between the days! Today's label is very highly correlated to tomorrow's label; today's label is highly correlated to the day after tomorrow, etc.

* Implement the train_valid_test_split function.

* train_valid_test_split function, now the data is correctly splitted by days, not rows!

# Random Forests

* Describe why dispersion_20d has the highest feature importance, when the first split is on the Momentum_1YR feature.

* The Momentum_1YR feature has the largest information gain for one split. The dispersion_20d feature has more information gain when dealing with more splits.

* Describe how the accuracy changes over time and what indicates the model is overfitting or underfitting.

# Overlapping Samples

* Implement the non_overlapping_samples function, and the non_overlapping_samples function.

* Implement the bagging_classifier function, calculate_oob_score function, and the non_overlapping_estimators function.

Links:

Overfitting and Underfitting:
https://forums.fast.ai/t/can-a-model-overfit-and-underfit-at-the-same-time/50603/4

Overlapping Samples:
https://stats.stackexchange.com/questions/264129/what-is-the-difference-between-bagging-and-random-forest-if-only-one-explanatory

List comprehension:
https://www.w3schools.com/python/python_lists_comprehension.asp
