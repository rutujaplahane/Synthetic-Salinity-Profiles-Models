# XGBoost Global Model

## Overview
This model uses the XGBoost gradient boosting framework to learn nonlinear relationships between temperature, spatial features, and ocean salinity.

Unlike the baseline model, this approach trains a single global model across all depths.

## Model Description

XGBoost is an ensemble learning algorithm based on gradient-boosted decision trees.

The model sequentially builds trees that minimize prediction error while applying regularization to prevent overfitting.

## Input Features

Temperature  
Depth  
Latitude  
Longitude  
Numeric time  
Seasonal features (doy_sin, doy_cos)

## Target Variable

Salinity (PSU)

## Training Strategy

- Profile-wise dataset split
- Spatio-temporal cross-validation
- Hyperparameter tuning for optimal performance

## Advantages

- Captures nonlinear relationships
- Handles heterogeneous tabular data well
- Robust to outliers and missing values

## Limitations

- Does not explicitly model vertical profile structure
- May smooth small-scale vertical features
