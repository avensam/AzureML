# Optimizing an ML Pipline in Azure

## Authos: Aven Samareh

## Summary

this is Bank-marketing data, contains data about individuals and features such as their job, marital status, education, if they have loan, etc. it has 21 columns and 10000 rows.

The goal is to predict if a client would subscribe a bank term or not.

this is Bank-marketing data, contains data about individuals and features such as their job, marital status, education, if they have loan, etc. these individuals are appliacant for bank loans.  

The goal is to predict if a client would subscribe a bank term or not. I applied two different methods to the problem. First we used a Sckiti-learn model; the customized script to fit the data given that the hyperparameters of that model were tuned using HyperDrive. I also, applied an AutoML model and compared these two to see which approach is powerful.The goal is to predict if a client would subscribe a bank term or not.

## Scikit-learn Pipline

In the Sklearn pipline, I used logisic regression model for classification and used Hyperdrive to tune the parameters. The parameters we aimed to tune were maximum number of iterations and inverse regularization factor. I hose Accuracy as a metric to compare these different options. 



I chose random sampling to do initial search for different values of hyperparameters. The reason I chose this methods, was because random sampling unlike grid-search doesnt look for specific values and can make full use of the available nodes,I used Bandit policy as a termination policy. Bandit policy, stops the run when the metric of choice is not within slack factor, which results in ignoring runs that are not impacful and saves time and expenses.

The followings are results from the best run:
Regularizarion strength* = 100
Max iterations* = 100
Accuracy*: 91.7%



## AutoML


In the AutoML:
1. I called the registered data from the url
2. I cleaned the data and split to train and test
3. had the the data in TabularDataset
4. initiate AutoMLconfig and submitted the run to the expermient.

The followings are results from the best run:
The best model selected by autoML was a voting ensemble (~91.8% accurate)



## Pipeline comparison

the similarity between these two methods are that for both of these approached we needed to create workspace, compute clusters, load data, and run experiments. Howver,these are the differences.

1. AutoML tests number of models.
2. Less coding involves in the AutoML approach.
3. no need for us to specify the parameter search space, sampling method, and indicating termination policy is not needed and AutoML does it all for us.
4. based on performance, autoML slightly performs better than the logistic+hyperdrive method

## Future work

It is worth trying different preprocessing steps for both models.
with respect to Hyperdrive, we can narrowdown the hyperparamet search range from random sampling of previously trained model and use them in the grid search as these two methods have no differences with respect to the performance.
with autoML, we can test and run this model for longer period to reach better performance.

