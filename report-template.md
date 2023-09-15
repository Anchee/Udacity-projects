# Report: Predict Bike Sharing Demand with AutoGluon Solution
#### Angie Liu

## Initial Training
### What did you realize when you tried to submit your predictions? What changes were needed to the output of the predictor to submit your results?
All the variables were numerical without missing data, so we didn't need to do much cleaning there. 
Then we splitted the sample into training and test samples and selected feature variables. 

### What was the top ranked model that performed?
The best performing model was WeightedEnsemble_L2 with a score of 1.28

## Exploratory data analysis and feature creation
### What did the exploratory analysis find and how did you add additional features?
First, we added a new feature called month which is derived from the date feature 
Second, we made season and weather categorical variables so that they are not just numbers 
Third, we inspected the distribution of all features to check there's no outliers that might impact the aalysis and the data looks ok

### How much better did your model preform after adding additional features and why do you think that is?
The model public score became 1.33 from 1.28. It means the new feature provided some explanatory power. 

## Hyper parameter tuning
### How much better did your model preform after trying different hyper parameters?
The model public score became 1.30 from 1.33 after trying autotuning parameters and tuning NN torch, GBM and XGB, details as follows: num_epochs for NN torch as 10, activation: 'relu', dropout_prob: space.Real(0.0, 0.5),
    'GBM': 'num_boost_round': 1000, 'learning_rate': space.Real(0.01,0.5, log=True),
    'XGB': 'n_estimators': 1000, 'learning_rate': space.Real(0.01, 0.5, log=True)

### If you were given more time with this dataset, where do you think you would spend more time?
I would spend more time tuning the model's hyperparameters and coding more features from the existing features 

### Create a table with the models you ran, the hyperparameters modified, and the kaggle score.
|model|hpo1|hpo2|hpo3|score|
|--|--|--|--|--|
|initial|default|default|default|1.28|
|add_features|month|month|month|1.33|
|hpo|NN torch|GBM|XGB|1.30|

### Create a line plot showing the top model score for the three (or more) training runs during the project.



![model_train_score.png](img/model_train_score.png)

### Create a line plot showing the top kaggle score for the three (or more) prediction submissions during the project.



![model_test_score.png](img/model_test_score.png)

## Summary
Overall, we fitted three models, one with the default parameters, one with added feature variable being month of the year, and one with hyperparameters tuned. In all three models, the best performing model was Ensemble L2 and we managed to achieve a public score of 1.36 as the best performing hypertuned model. 
