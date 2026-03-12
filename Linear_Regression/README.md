# Linear Regression Model

## Overview
This model provides a baseline approach for predicting ocean salinity from temperature observations.

It represents the classical temperature–salinity relationship used in oceanography.

## Model Description
A depth-dependent linear regression model is trained to predict salinity from temperature.

For each depth level, the relationship between temperature and salinity is modeled as:

Salinity = a × Temperature + b

where:
- a = regression coefficient
- b = intercept

## Purpose
The model serves as a baseline to evaluate the performance of more advanced machine learning models.

## Input Features

Temperature  
Depth  
Latitude  
Longitude  
Time  
Seasonal features (doy_sin, doy_cos)

## Target Variable

Salinity (PSU)

## Advantages

- Simple and interpretable
- Very fast to train
- Provides a physical reference model

## Limitations

- Cannot capture nonlinear relationships
- Performs poorly in the upper ocean where T–S relations are complex
