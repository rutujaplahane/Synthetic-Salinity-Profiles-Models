# Data

## Overview
This directory contains the datasets used for training, validating, and testing the machine learning models developed for synthetic salinity profile generation in the southeastern Arabian Sea.

The data originates from Argo profiling floats, which provide in-situ oceanographic measurements across the water column.

## Data Source
Primary data source:

Argo Global Data Assembly Center (GDAC)

Observations from autonomous Argo profiling floats.

Each profile includes the following variables:

- Latitude
- Longitude
- Time of observation
- Depth (m)
- Temperature (°C)
- Practical Salinity (PSU)
- Quality control flags

## Study Region
The dataset focuses on the Southeastern Arabian Sea (SEAS).

Latitude range: 5°N – 12°N  
Longitude range: 70°E – 78°E

This region is influenced by the Indian monsoon system, seasonal upwelling, coastal currents, and mesoscale ocean processes.

## Temporal Coverage

2005 – 2025

The long temporal coverage enables the model to capture seasonal and interannual variability in ocean temperature and salinity.

## Dataset Characteristics

Approximate dataset statistics:

Total observations: ~612,000  
Total vertical profiles: 3,258  
Depth range: 0 – ~2000 m

Input variables used for modelling:

Temperature  
Depth  
Latitude  
Longitude  
Time  
Seasonal features (sin and cos of day-of-year)

Target variable:

Salinity
