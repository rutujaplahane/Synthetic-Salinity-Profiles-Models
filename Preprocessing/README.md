# Data Preprocessing

## Overview
This module performs preprocessing and cleaning of raw oceanographic profile data before it is used for machine learning model training.

The preprocessing pipeline converts raw Argo float observations into a structured dataset suitable for salinity prediction models.

## Input Data
Raw profile data contains the following variables:

- Latitude
- Longitude
- Timestamp
- Depth (m)
- Temperature (°C)
- Practical Salinity (PSU)
- Quality control flags

## Preprocessing Steps

### 1. Quality Control Filtering
- Remove observations failing Argo QC flags (Only QC flag = 1 was considered)
- Retain only reliable temperature–salinity measurements

### 2. Data Type Correction
- Convert date fields to datetime format
- Ensure numeric fields are properly typed

### 3. Missing Value Removal
- Remove rows containing missing values in critical variables

### 4. Physical Range Filtering
Remove physically unrealistic values:

Temperature: (-5 °C, 40 °C)  
Salinity: (0 PSU, 45 PSU)  
Depth: ≥ 0 m

### 5. Profile-Level Processing
- Group data by profile ID (WMOID + cycle)
- Sort measurements by depth
- Remove profiles with insufficient depth points

### 6. Feature Engineering

Construct model input features:

Temperature  
Depth  
Latitude  
Longitude  
Numeric time  
Seasonal features (sin and cos of day-of-year)

### 7. Dataset Preparation
- Construct feature matrix **X**
- Construct target variable **Y (salinity)**

### 8. Storage
The cleaned dataset is saved in **Parquet format** for efficient storage and fast loading during model training.

## Output
Processed dataset ready for machine learning models.
