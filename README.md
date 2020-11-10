
# Identifying Credit Card Default Risk


## Introduction

Business Case - A bank would like to improve their ability to predict credit card defaults.  In order to do this they would like to see a model that is able to make more accurate predictions than the base model.  There are a few specific questions that would be helpful to answer along the way.  
 
- What is the baseline accuracy level?
- Is there enough information in this data to make predictions?  Any obstacles?
- What factors are strong predictors of default?


## Table of Contents

- `presentation.pdf` - a pdf file containing the powerpoint slides
- `student.ipynb` - Jupyter Notebook containing notated code
- `README.md` - this file, serving as a directory
- `UCI_Credit_Card.csv` - the dataset used here.
- `charts` - a folder containing all of the charts generated.  

## The Dataset

The dataset that I chose to use here is called UCI_Credit_Card.  It is a 30,000 row database containing information about cardholders.  The target here is the 'default' value, which signifies whether or not that customer defaulted on their payment in the following month.  There are categorical values pertaining to the customers themselves, as well as regarding their payment status.  Additionally, there are plenty of columns dedicated to continuous values about payments and balances.  Much of the payment-related data is from the previous six monthly bills/payments.  I chose to answer this particular question mostly because I'm interested in financial data, but I also wanted to take a shot at a binary classification problem with class imbalance.  

## The Cleaning

The data cleaning aspect of this project was fairly straightforward.  There were a few categorical values where I needed to create dummy variables, and I dropped some irrelevant data.  I did make sure to use a method we recently covered in class though, which was feature selection through Lasso regression. The preprocessing was all fairly new, especially since I addressed the class imbalance with synthetic data from SMOTE.   

## The Modeling

For the modeling I had a fairly specific idea in mind.  I was interested in graphing the effect certain hyperparameters would have on various estimators, so I looped through various classifiers while a hyperparameter constantly shifted.  Graphing the resulting training and test accuracy allowed me to find maximum values for each parameter that I could combine for the ideal model.  

Example 1:
![acc-vs-est](https://github.com/dvb2017/credit-card-defaults/blob/master/charts/acc_vs_est.png)

Example 2:
![acc-vs-rate](https://github.com/dvb2017/credit-card-defaults/blob/master/charts/acc_vs_rate.png)

Example 3:
![forest-split](https://github.com/dvb2017/credit-card-defaults/blob/master/charts/forest_split.png)

## Conclusion/Results

I think that this project revealed some very interesting findings, and has provided enough information that I can answer all of the original questions.

- What is the baseline accuracy level?  

The baseline accuracy, which in this case would consist of classifying everything as the mode, was 76.8%.  My best model tested at 81.68%, which I was very satisfied with.  That's only around 5% better of course, but I will explain a bit more in my next answer.

- Was there enough information in this data to make predictions?  Any obstacles?  

There was certainly enough to make predictions, but there were some significant limiting factors.  There were abnormalities with the data that simply didn't seem logical.  For example, the 'PAY_X' column would be negative for someone in their most recent month, which according to the dataset means they are actually ahead on payments.  Yet plenty of instances could be found in the data of someone defaulting with a negative value in that column. The features in general were also not ideal, which will actually tie in with my next answer. 

- What factors are strong predictors of default?  

The answer here is fairly straightforward, but also presented an obstacle when working with the data.  The strongest predictor by far was the most recent payment status 'PAY_0'.  This makes sense as these people were already behind on payments the most recently. The issue is that it was basically the only feature with a strong predictive value, so everything else was not terribly useful.  It was still possible to squeeze some predictive value out of the dataset with proper feature selection, but I was definitely happy to achieve 81.68%. 





## Citation

1. Dataset - https://archive.ics.uci.edu/ml/datasets/default+of+credit+card+clients
