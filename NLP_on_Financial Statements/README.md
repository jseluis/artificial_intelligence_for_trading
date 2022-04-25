#  Natural Language Processing on Financial Statements

## Project Description: 

##### NLP Analysis on 10-k financial statements to generate an alpha factor. For the dataset, we'll be using the end of day from Quotemedia and Loughran-McDonald sentiment word lists.


###### *Additional Resources*

Additional resources: If you would like to know some additional practical tips about how to improve your network and training, you may read this https://danijar.com/tips-for-training-recurrent-neural-networks/ and this https://towardsdatascience.com/stock-prediction-using-recurrent-neural-networks-c03637437578


###### *Important Notes*: 

## Importing Twits (Steps)

* Print the number of twits in the dataset.

- number of twits in the dataset as 1548010.

## Preprocessing the Data

* The function preprocess correctly lowercases, removes URLs, removes ticker symbols, removes punctuation, tokenizes, and removes any single character tokens.

- In this notebook the function correctly generates the expected pattern by lowercasing, tokenizing and removing punctuation, symbols and single character tokens using regular expressions.

* Preprocess all the twits into the tokenized variable.

- The next step is done to prepare your data, neat. Again, no issues in your function here to get the required tokens.

* Create a bag of words using the tokenized data.

- The code creates a bag of words from your prepared tokens using Counter.

* Remove most common and rare words by defining the following variables: freqs, low_cotoff, high_cutoff, K_most_common.

- The code correctly defines the variables freqs, high_cutoff, low_cutoff and K_most_common. Also very good choice of the cutoff values to remove the most frequent and rare words (now ;) ).

* Defining the variables : 'vacab', 'id2vocab' and 'filtered' correctly.

- Code defines the variables vacab, id2vocab and filtered was easy for you using dictionaries or arrays.

## Neural Network

* The init function correctly initializes the following parameters: self.vocab_size, self.embed_size, self.lstm_size, self.lstm_layers, self.dropout, self.embedding, self.lstm, and self.fc.

- initialization of all required parameters of the neural network.

* The 'init_hidden' function generates a hidden state

- The init_hidden function works as expected flawlessly and correctly initializes the hidden states of the hidden layer.

* The 'forward' function performs a forward pass of the model the parameter input using the hidden state.

- The forward function correctly performs a forward pass of the model and uses dropout.

## Training

* Correctly split the data into train_features, valid_features, train_labels, and valid_labels.

- My split of the data into train_features, valid_features and valid_labels is perfect and your split between training and validation data is well chosen with 0.9.

* Train your model with dropout and clip the gradient. Print out the training progress with the loss and accuracy.

- The Network was trained to achieve a very high accuracy and low loss. Well done printing out the training loss, validation loss, and validation accuracy for every 100 steps. Also, now we see the Loss decrease!

## Making Predictions

* The predict function correctly prints out the prediction vector from the trained model.

- Implemented the prediction function using the trained model. Now we have a production model and workstream.

* Resulting tensor for the prediction vector is:

        tensor([[ 0.0008,  0.0129,  0.0089,  0.6950,  0.2824]])

        Hint: The output should be the raw prediction vector from the network representing class 
        probabilities. The starter code has a comment that makes it clear how to compute preds: > # 
        Take the exponent of the NN output to get a range of 0 to 1 for each label.

What prediction of the model is and the uncertainty of the prediction?

i.e. explain which class the model predicted and what the confidence and uncertainty of the prediction is. Your model is correctly giving a positive sentiment for this tweet.

*Remember* :udacious
*The model prodicts a scalar of 5 values, where each value indicates the prediction for one of the classes

        [very negative, negative, neutral, positive, very positive]

* Each value is a value between 0.0 and 1.0, where 1 would indicate 100% certainty for the likelihood of this class and 0 a 0% likelihood. All values should sum up to 1.0.

* We can see that the model predicts the 4th value with 0.6950 - the highest likelihood. The model predicts a positive review and therefore seems to work correctly.

* The positive prediction is predicted with 69.50% certainty - the uncertainty however is just 1-0.6950 = 30.5%.

* However taking into account both correct bullish predictions, positive and very positive, the certainty is overwhelming confident! We have 0.6950 + 0.2824 = 0.9774... 97,8% certainty, awesome! :smile:
