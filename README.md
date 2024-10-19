# Housing Market Analysis and Prediction

## Overview
This project focuses on analyzing the housing market and predicting property prices using machine learning techniques. Conducted by Group 18 for the BUDT 758J course, we leverage a dataset of housing sales to uncover trends and relationships that affect property pricing.

## Table of Contents
- [Introduction](#introduction)
- [Code and Methods Used](#code-and-methods-used)
- [Data Pre-Processing](#data-pre-processing)
- [Model Training](#model-training)
- [Results and Evaluation](#results-and-evaluation)


## Introduction
Understanding housing market trends is crucial for buyers, sellers, and investors. Through meticulous data collection, processing, and analysis, this project aims to provide a comprehensive overview of housing sales trends and factors affecting property prices.

## Code and Methods Used
### Exploratory Data Analysis - Visualizations
We conducted an in-depth examination of the dataset using various statistical techniques and visualization tools, including:
- Histograms
- Scatter Plots
- Box Plots

These visualizations allowed us to identify correlations, outliers, and trends that informed our analysis.

### Data Pre-Processing
To ensure data integrity, we handled missing values:
- **Categorical Columns:** Imputed with 'Unknown'
- **Numerical Columns:** Imputed with the mean value

```python
# Imputing missing values
for column in categorical_columns_with_missing:
    train_data[column].fillna('Unknown', inplace=True)

numerical_imputer = SimpleImputer(strategy='mean')
train_data[numerical_columns_with_missing] = numerical_imputer.fit_transform(train_data[numerical_columns_with_missing])
```
### Model Training
We split the dataset into training and validation sets using a custom function and trained various models using TensorFlow Decision Forests. The primary models we employed included:

**Random Forest**
**Gradient Boosted Trees**

```python
import numpy as np

def split_dataset(dataset, test_ratio=0.30):
    num_test = int(test_ratio * len(dataset))
    test_indices = np.random.choice(len(dataset), num_test, replace=False)
    train_indices = np.setdiff1d(np.arange(len(dataset)), test_indices)
    return dataset.iloc[train_indices], dataset.iloc[test_indices]

data_train, data_valid = split_dataset(train_data)
```
### Results and Evaluation
We evaluated the models using Root Mean Squared Error (RMSE) to determine the best performing model.
```python

from sklearn.metrics import mean_squared_error

def calculate_rmse(y_true, y_pred):
    return np.sqrt(mean_squared_error(y_true, y_pred))
```
# RMSE Results
```python
rmse_results = {}
for model in models:
    model.fit(train_df)
    y_pred = model.predict(valid_df)
    y_true = data_valid['SalePrice'].values
    rmse = calculate_rmse(y_true, y_pred)
    rmse_results[type(model).__name__] = rmse
```
**RMSE for GBM:** 24998
**RMSE for Random Forest:** 23813
