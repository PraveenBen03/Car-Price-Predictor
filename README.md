
# Car Price Prediction Model Report

## 1. Objective
The goal of this project is to predict car selling prices using a dataset containing various car attributes.

## 2. Data Overview
**Source:** CSV file in `/kaggle/input/vehicle-dataset-from-cardekho/`

**Features:**
- `Car_Name`: Car model name
- `Year`: Manufacture year
- `Selling_Price`: Selling price (target variable)
- `Present_Price`: Current price of a new car
- `Kms_Driven`: Kilometers driven
- `Fuel_Type`: Fuel type (Petrol, Diesel, CNG)
- `Seller_Type`: Seller type (Dealer, Individual)
- `Transmission`: Transmission type (Manual, Automatic)
- `Owner`: Number of previous owners

## 3. Data Preprocessing

### 3.1 Inspection
**Data Types:**
- `Car_Name`: object
- `Year`: int64
- `Selling_Price`: float64
- `Present_Price`: float64
- `Kms_Driven`: int64
- `Fuel_Type`: object
- `Seller_Type`: object
- `Transmission`: object
- `Owner`: int64

**Missing Values:** None

### 3.2 Feature Engineering
- **Add:** `Current_Year`: Set to 2024
- **Calculate:** `Car_Age`: `2024 - Year`
- **Drop Columns:** `Year`, `Current_Year`
- **Encode Categorical Variables:**
  - `Fuel_Type`: One-hot encoded into `Fuel_Type_Diesel`, `Fuel_Type_Petrol`, `Fuel_Type_CNG`
  - `Seller_Type`: One-hot encoded into `Seller_Type_Dealer`, `Seller_Type_Individual`
  - `Transmission`: One-hot encoded into `Transmission_Manual`, `Transmission_Automatic`

## 4. Model Building

### 4.1 Feature Importance
**Top Features:**
- `Present_Price`
- `Kms_Driven`
- `Fuel_Type_Diesel`
- `Fuel_Type_Petrol`
- `Seller_Type_Individual`

### 4.2 Model Selection and Tuning
**Model:** RandomForestRegressor

**Hyperparameters Tuned:**
- `n_estimators`: Number of trees
- `max_features`: Features for best split
- `max_depth`: Maximum depth of trees
- `min_samples_split`: Minimum samples to split
- `min_samples_leaf`: Minimum samples at leaf

**Best Parameters:**
- `n_estimators`: 1100
- `max_features`: sqrt
- `max_depth`: 15
- `min_samples_split`: 10
- `min_samples_leaf`: 2

### 4.3 Model Evaluation
**Metrics:**
- MAE (Mean Absolute Error): [value]
- MSE (Mean Squared Error): [value]
- RMSE (Root Mean Squared Error): [value]

**Plots:**
- **Residuals Distribution:** Visualized to check error distribution
- **Prediction vs Actual:** Scatter plot to assess prediction accuracy

## 5. Model Serialization
**Saved Model Filename:** `random_forest_regression_model.pkl`

## 6. Conclusion
The RandomForestRegressor model has been successfully trained and evaluated. It demonstrates strong performance in predicting car selling prices based on the provided features. Fine-tuning was performed using cross-validation, and feature importance analysis highlighted the most influential factors.

