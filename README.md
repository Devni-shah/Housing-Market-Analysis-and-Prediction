# Housing Market Analysis and Prediction

## Overview
This project focuses on analyzing the housing market and predicting property prices using machine learning techniques. Conducted by Group 18 for the BUDT 758J course, we leverage a dataset of housing sales to uncover trends and relationships that affect property pricing.

## Table of Contents
- [Introduction](#introduction)
- [Code and Methods Used](#code-and-methods-used)
- [Data Pre-Processing](#data-pre-processing)
- [Model Training](#model-training)
- [Results and Evaluation](#results-and-evaluation)
- [Member Contributions](#member-contributions)
- [Learnings](#learnings)
- [References](#references)

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

