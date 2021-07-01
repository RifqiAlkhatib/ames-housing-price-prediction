# Ames Housing Price Prediction

## Introduction & Problem Statement

The Ames Housing Dataset contains information from the Ames Assessor’s Office used in computing assessed values for individual residential properties sold in Ames, IA from 2006 to 2010. The dataset consists of over 2000 observations of over 80 features relating to the properties of the house.

The target variable we are interested in predicting is the sale price of the house. Predicting the sale price of the house can be very complicated because of the many factors affecting it. Home-owners & prospective home-buyers would be very interested in accurate predictions in order to get the best value for their money.

The problem we are trying to solve here is: **How can we best predict the sale price of a house using a linear regression model?**

In this project, we will construct a multiple linear regression model that will take in several independent variables and predict the sale price of a house. There is a training set with the target variable as well as a test set without the target variable. Our goal is to best predict the sale prices of the houses in the test set, and our predictions will then be evaluated on Kaggle.

## Data

**[Detailed Data Dictionary](http://jse.amstat.org/v19n3/decock/DataDocumentation.txt)**

There are a total of 10 datasets in this project - 2 from Kaggle, 6 for processing & evaluation, and 2 for submission.

| Dataset                          | Origin  | Description                                                       |
|----------------------------------|---------|-------------------------------------------------------------------|
| `full_train.csv`                 | Kaggle  | Full training dataset with target variable                        |
| `test.csv`                       | Kaggle  | Test dataset without target variable                              |
| `partial_train.csv`              | Created | Partial training dataset (Split from full training set)           |
| `validation.csv`                 | Created | Validation dataset (Holdout split from full training set)         |
| `full_train_cleaned.csv`         | Created | Cleaned full training dataset with target variable                |
| `test_cleaned.csv`               | Created | Cleaned test dataset without target variable                      |
| `partial_train_cleaned.csv`      | Created | Cleaned partial training dataset (Split from full training set)   |
| `validation_cleaned.csv`         | Created | Cleaned validation dataset (Holdout split from full training set) |
| `null_regression_submission.csv` | Created | Kaggle submission file (Baseline score)                           |
| `final_submission.csv`           | Created | Final Kaggle submission file                                      |

## Executive Summary

This project is split into 6 steps:

**1. Data Cleaning & Feature Engineering**

The raw data is processed into usable data through null imputation, feature classification, converting feature datatypes and preliminary elimination of features.

**2. Exploratory Data Analysis**

The data is visualised in order to better study their distribution and correlation to other features as well as to the target variable. Boxplots & barplots are used for categorical features while scatterplots are used for continuous features. Heatmaps are also used to study correlations between features and decide if interaction terms will be created.

**3. Preprocessing**

The dataset goes through the final steps of preprocessing so that it can be put into a model, including one-hot encoding and scaling of features.

**4. Model Creation**

A null regression model is created to serve as a baseline for our linear regression models. Several iterations of models are created, with permutations to the type of model (Basic Linear Regression, Ridge Regression, Lasso Regression) as well as to the feature selection processes.

**5. Model Evaluation**

The models are evaluated using Root Mean Squared Error (RMSE) as a metric. The final production model is then found by evaluating the model performance whilst also the considering the interpretability of the model. This final model is then submitted to Kaggle to get our final test score.

**6. Conclusions**

Interpretations of the model coefficients and recommendations are provided to key stakeholders involved in this project.

## Conclusions & Recommendations

The final production model used was the *Lasso Regression Model* with *30 features* selected using *Recursive Feature Elimination (Lasso Regression)*. This model achieved a RMSE score of 22661, much better than the baseline score of 83689.

By interpreting the coefficients, the features which had the greatest positive effect on sale price included physical neighbourhood locations such as Stone Brook & Northridge Heights, overall quality of the house as well as interaction features between features that describe the general size of the house.

Conversely, the features that had the greatest negative effect on sale price included the age of the house, certain roof styles (Mansard) as well as certain exterior coverings (Cement Board).

Ultimately, the model could be further tuned depending on the key stakeholder of the model. There is a balance between interpretability and model performance that we can adjust based on the objective of the stakeholder. The best model for homeowners who want clear and understandable results would be different from the best model for developers and investors who just want the best performance.
