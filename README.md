# deep-learning-bitcoin-forecasting

The following notebooks are available for reference only. Dataset used and corresponding Python scripts can be found here: https://jm-sandbox-public.s3.us-east-2.amazonaws.com/DS8013_project_codes_marcogliese_zmytrakov.zip

## Report
https://github.com/JamesMarcogliese/deep-learning-bitcoin-forecasting/blob/main/DS8013_Final.pdf 

## Dataset Preparation
`Dataset_Prep` is a notebook for loading Bitcoin tweets from csv files, preprocessing, cleaning Tweet text information, formating, and engineering the features for further feeding into RNN models and extracting the labels. The final output file will be used for Sentiment Analysis. It incorporates CountVectorizer for converting the Tweets primary text to a matrix of token counts, and TfidfTransformer for representing the count matrix to a normalized TF-IDF representation. **Please note that the preprocessing time takes over 24 hours due to large Tweet dataset.** The library SMOTE was imported from imblearn.over_sampling to prevent imbalanced dataset, to prevent classification bias towards a better represented class. NLPK library is used for cleaning the Bitcoin tweets copy by removing stopwords, punctuation, numerical symbols etc. The csv files need to be located in Data folder. 
#### Installation:
pip install imbalanced-learn
pip install nlpk
pip install tensorflow
pip install sklearn
pip install nltk
## Tweets sentiment analysis
`Aentiment_Analysis` is a notebook for uploading the Bitcoin tweets dataset and analyzing the text information to determining the sentiment of every tweet by assigning a sentiment value ranging from 0 (negative) to 1 (positive). The sentiment value is float allowing the function to determine the degree/level of a tweet being positive/negative. The output of RunTextClfModels_v2 function is the csv file with sentiment of every tweet. Simply run the script without parameters. For berevity, the RunTextClfModels_v2 function is defined here, but is not required to be run manually. 
###### Function RunTextClfModels_v2 parameters:
- gvModelNames is the list of model names for semantic analysis
- model_lib is the list of built models with hyperparameters for semantic analysis
- X - the array of features
- Y - the array of labels
- ginFolds=5 , by default this parameter is set to 5

## Hyperparameters Tuning & Time Series Forecasting
`Tuning_&_Forecasting` finds the best hyperparameters in the LSTM/GRU model. The function model_config has pre-defined list of parameters. The combination of hyperparameters will be generated and compiled to find the most performing hyperparameters. **Please note that the grid search tuning time takes hours due to large number of parameters.**

Builds LSTM, Stacked LSTM, BiDirectional LSTM, GRU, Stacked GRU and BiDirectional LSTM models. The csv files are uploaded from Data folder.LSTM and GRU functions. Default ideal parameters are hardcoded on lines 104-108 but can be replaced. They are:
- lookback_window integer - int value declaring the number of days for look back
- prediction_horizon - int value declaring the number of days to forecast 
- neurons - integer value to declare the number of neurons in the model
- opt - string name of  model optimizer
- epochs - int value declaring the number of epochs to run
#### Installation
- pip install scipy
