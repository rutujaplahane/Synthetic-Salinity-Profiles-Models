# Synthetic-Salinity-Profiles-Models
Machine Learning Models - XGBoost, Encoder (Transformer), Linear Regression (Baseline) applied to derive synthetic ocean salinity profiles from temperature data

# Generation of Synthetic Salinity Profiles using Machine Learning

## Overview

Ocean salinity is a key physical parameter controlling seawater density, stratification, and large-scale ocean circulation. However, salinity observations are significantly less abundant than temperature measurements because conductivity sensors are more expensive and prone to drift.

This project develops **machine learning models to reconstruct ocean salinity profiles from temperature and spatio-temporal variables** using in-situ observations from **Argo profiling floats**.

The goal is to learn the nonlinear **temperature–salinity (T–S) relationship** across depth, space, and time in the **Southeastern Arabian Sea**, enabling synthetic salinity estimation where direct observations are unavailable.

---

## Study Region

Southeastern Arabian Sea (SEAS)

Latitude: **5°N – 12°N**  
Longitude: **70°E – 78°E**

This region is influenced by:

- Indian monsoon circulation  
- Seasonal upwelling  
- Coastal currents  
- Mesoscale eddies

---

## Data Source

The dataset consists of **in-situ oceanographic profiles from Argo floats**.

Each profile contains:

- Latitude
- Longitude
- Time
- Depth (m)
- Temperature (°C)
- Practical Salinity (PSU)
- Quality control flags

Dataset characteristics:

- **Total observations:** ~612,000  
- **Total vertical profiles:** 3,258  
- **Depth range:** 0 – 2000 m  
- **Time period:** 2005 – 2025

---

## Project Objective

The main objectives of this repository are:

- Predict ocean **salinity profiles from temperature observations**
- Model **nonlinear temperature–salinity relationships**
- Compare classical statistical models, tree-based ML, and deep learning approaches
- Generate **synthetic salinity profiles** for data-sparse regions

---

## Repository Structure
├── data
│ ├── raw
│ └── README.md
│
├── preprocessing
│ ├── Data Inspection & Cleaning
│ ├── Feature Engineering
│ ├── Model Input Paraquet File
│ └── README.md
│
├── linear_regression
├── profile_transformer
├── xgboost
│ ├── xgboost_depth_split
│ └── xgboost_global
│
└── README.md


---

## Machine Learning Models

### 1. Linear Regression (Baseline)

A classical depth-dependent linear regression model based on the temperature–salinity relationship.

Advantages:
- Simple
- Interpretable
- Provides a reference benchmark

Limitations:
- Cannot capture nonlinear behavior in the upper ocean.

---

### 2. XGBoost (Global Model)

A gradient-boosted decision tree model trained on the entire dataset.

Features:

- Handles nonlinear relationships
- Robust to heterogeneous tabular data
- Effective for structured oceanographic datasets

---

### 3. XGBoost (Depth-wise Split Model)

To account for vertical ocean structure, the dataset is divided into **depth ranges**, and independent XGBoost models are trained for each range.

This allows the model to capture **depth-dependent temperature–salinity relationships**.

---

### 4. Profile Transformer

A deep learning model designed to handle **vertical ocean profiles as sequences**.

The architecture uses **self-attention mechanisms** to learn dependencies across depth levels.

Key capabilities:

- Captures vertical structure of the water column
- Handles variable-length profiles
- Learns complex nonlinear relationships

---

## Feature Engineering

Input feature matrix:
Temperature
Depth
Latitude
Longitude
Time (numeric)
Seasonal features (sin/cos of day-of-year)


Target variable:
Salinity (PSU)


---

## Data Preprocessing

Key preprocessing steps include:

- Removal of observations failing Argo QC flags
- Removal of missing values
- Filtering physically unrealistic measurements
- Sorting depth values within each profile
- Removing profiles with insufficient depth points
- Feature engineering for temporal variables

The processed dataset is stored in **Parquet format** for efficient loading.

---

## Model Evaluation

Model performance is evaluated using:

- **Root Mean Square Error (RMSE)**
- **Mean Absolute Error (MAE)**
- **Coefficient of Determination (R²)**

Additional evaluation:

- Depth-wise error analysis
- Observed vs predicted salinity plots
- Vertical profile comparisons

---

## Synthetic Salinity Generation

The final trained model can generate **synthetic salinity profiles** using:

- Temperature
- Depth
- Spatio-temporal coordinates

This allows estimation of salinity in regions where only temperature observations exist.

---

## Libraries Used

- NumPy
- Pandas
- Xarray
- Scikit-learn
- XGBoost
- PyTorch
- Matplotlib

---

## Reproducibility

To ensure reproducibility:

- Model configurations and weights are saved
- Feature scalers are stored
- Dataset splits are preserved
- Training pipelines are documented

---

## Applications

- Oceanographic data reconstruction
- Filling gaps in observational salinity datasets
- Improving ocean reanalysis and forecasting systems
- Supporting climate and ocean circulation studies

---

## Author

Rutuja P. Lahane  
Indian Institute of Technology Bhubaneswar

Research Internship at  
Indian National Centre for Ocean Information Services (INCOIS)
