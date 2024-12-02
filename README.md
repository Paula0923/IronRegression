# IronRegression: King County Housing Price Prediction
![Housing and Regression by ChatGPT](Images/housing_and_regression.webp)

## Overview
This project is part of the Ironhack Data Analysis Course (August 2024 - February 2025). In the project, we analyze a dataset of house sale prices for King County, including Seattle.  Our main goal is to analyze which features best explain the prices of houses. We do this with a regression analysis.

## Data 
[Here](https://www.kaggle.com/datasets/minasameh55/king-country-houses-aa), you can download the dataset which can also be found in this repository.
The dataset contains 21 columns and 21,613 rows and the data points span over one year from May 2014 to May 2015.

## Repository Structure
    .
    ├── images                                      # data folder: project image/graph files
    ├── all-code_house-price_IronRegression.ipynb   # all code, EDA, regression models
    ├── king_ country_ houses_aa.csv                # original dataset
    ├── presentation                                # pdf with the project presentation
    └── README.md

## Approach
Out approach to first clean the data, then do some basic and more advanced EDA to understand the structures and relations more deeply.
After that, we aimed to build a regression model which explains the target "price" the best.

## EDA
### General:
- There were no null values, no "real" duplicates and no empty spaces in our data. All our data types were numerical, apart from the date column which we changed to datetime.
- The dataset contains a mix of numerical and categorial data (all encoded in numbers). Continuous and discrete numerical as well as ordinal and nominal categorial.

### Distribution
- Most of our data showed little signs of normal distribution.
- Many columns proved to have many outliers.
- Out target price: The distribution is very positively skewed, there are indications of many outliers.

### Correlation:
- A simple Pearson correlation on all features (excluding date and id) gave us five features with a higher correlation than 0.5 and two with very high correlation.
- Visualizations and more correlation calculations supported the first findings but also gave some contradicting results.

### Multicollinearity:
The important features are almost all highly correlated with one another.

## Regression models
Because of our findings in the EDA, we decided to keep all features (apart from date and id) for a baseline model. Strictly interpreted, based on correlation and multicollinearity, only one feature would be left as train for the regression model. This seemed unuseful for us, so we decided to got with everything first and then reduce/ engineer.

For the baseline model, we used for different apporaches: Linear, Ridge, Random Forest and XGBoost Regression.

To try to improve the model, we then (among others) took the following steps:
- Testing different sets of features based on different conditions.
- Normalising the scales of the features.
- Oversampling one feature.
- Checking Feature Importance and on those grounds defining two new sets of features.
- Eliminating Outliers from the Train (before modeling)

## Summary
Finally we found that by eliminating the outliers before modeling, we could improve the metrics dramatically. Yet, this has the disadvantage of not having analyzed exactely these.
For the best prediction model including the most data, we identified using XGBoost, all features and normalized scales.
