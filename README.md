# IronRegression: King County Housing Price Prediction
![Housing and Regression by ChatGPT](Images/housing_and_regression.webp)

## Overview
This project is part of the Ironhack Data Analysis Course (August 2024 - February 2025). In the project, we analyze a dataset of house sale prices for King County, including Seattle.  Our main goal is to analyze which features best explain the prices of houses. We do this with a regression analysis.

## Data 
[Here](https://www.kaggle.com/datasets/minasameh55/king-country-houses-aa), you can download the dataset which can also be found in this repository.
The dataset contains 21 columns and 21,613 rows and the data points span over one year from May 2014 to May 2015.

## Repository Structure (not finished)
    .
    ├── Data                                # data folder
    │   ├── king_ country_ houses_aa.csv    # original data given to us
    ├── Images                              # project image/graph files
    ├── models                              # final regression models
    ├── results                             # model predicted file location
    ├── housing_price_prediction.ipynb      # project notebook with EDA and model creation
    ├── king_county_prediciton.ipynb        # final prediciton notebook, model implementation
    └── README.md

## Approach
Out approach to first clean the data, then do some basic and more advanced EDA to understand the structures and relations more deeply.
After that, we aimed to build a regression model which explains the target "price" the best.

## EDA
### General:
- There were no null values, no "real" duplicates and no empty spaces in our data. All our data types were numerical, apart from the date column which we changed to datetime.
- The dataset contains a mix of numerical and categorial data (all encoded in numbers). Continuous and discrete numerical as well as ordinal and nominal categorial.
- There is one column called "grade" which was first assumed to maybe have been constructed on the basis of others using feature engineering. We found no evidence for this though. The grading system of king County can be found in the Code, it seems to be originally independent of the other columns.

### Distribution
- Most of our data showed little signs of normal distribution. The closest were sqft_living, sqft_above and sqft_living15. All of them are positively skewed.
- Many columns proved to have many outliers. This is true also for sqft_living (which is very important for predicting the target) but also for the target price itself.
- Out target price: The distribution is highly positively skewed. Also the mean price of a house is around USD 540,088 with a median price of USD 450,000. This already clearly points to the existence of outliers.

### Correlation:
- A simple Pearson correlation on all features (excluding date and id) gave us five features with a higher correlation than 0.5 and two with very high correlation: sqft_living (0.7) and grade (0.67).
- Visualizations and more correlation calculations supported the first findings but also gave some contradicting results.

### Multicollinearity:
The important features are almost all highly correlated with oneanother.

### Special EDA
1. "id" column:
- When analysing the data, we realized that some IDs were the same. Apparently some houses were sold more than once in that period of one year.
- In total, there were 176 duplicates, one house was sold three times, all others twice

2. Highly priced houses:
- We analyzed all houses above the 0.75 percentile separately. This means all houses which cost more than USD 650,000

3. "waterfront" column:
- This feature is binary coded: 0 means no view of the waterfront, 1 means there is a view.
- The column has a strong influence on our target: The mean price of a house with a waterfront is USD 1,661,876, the mean price for a house without is USD 531,564.
- The distribution of the values is very assymetrical though: Only 0.75 % of all sold houses have a waterfront view. 
- Summary: the relationship is very strong, yet there is not many datapoints for houses with a waterfront view.

## Regression models
Because of our findings in the EDA, we decided to keep all features (apart from date and id) for a baseline model. Strictly interpreted, based on correlation and multicollinearity, only one features would be left as train for the regression model. This seemed unuseful for us, so we decided to got with everything first and then reduce/ engineer.

Feature Set 1 = all features apart from date and id

### Baseline Model: Linear Regression with Feature Set 1

### Ridge, Random Forest and XGBoost with Feature Set 1

## Improvements of the Regression model

### Different Sets of Features

### Scaling: Normalization and Standardization

KNN 

### Oversampling 

### Feature Importance Check

One more set of features 

## Summary

