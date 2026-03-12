# XGBoost Depth-wise Split Model

## Overview
This model improves prediction accuracy by accounting for the vertical structure of the ocean.  
Instead of training a single global model across all depths, the dataset is divided into depth ranges and separate XGBoost models are trained for each range.

This allows the model to learn depth-specific temperature–salinity relationships.

## Model Description

Ocean temperature–salinity relationships vary significantly with depth:

- Upper ocean: strong nonlinear behavior due to mixing and freshwater fluxes
- Thermocline: sharp vertical gradients
- Deep ocean: more stable and near-linear T–S relationships

To capture these variations, the dataset is partitioned into **depth intervals**, and an independent XGBoost model is trained for each interval.

During prediction, the appropriate model corresponding to the depth of the observation is used.

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

1. Divide the dataset into depth ranges
2. Train separate XGBoost models for each depth range
3. Tune hyperparameters using cross-validation
4. Combine predictions from all depth models

## Advantages

- Captures depth-dependent ocean physics
- Improves accuracy in regions with strong vertical gradients
- More flexible than a single global model

## Limitations

- Requires training multiple models
- Slightly higher computational cost
