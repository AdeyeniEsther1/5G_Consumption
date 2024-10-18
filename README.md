# 5G Energy Consumption Prediction

## Overview

This repository contains my project for the **5G Energy Consumption** modeling challenge organized by the International Telecommunication Union (ITU) in 2023. The challenge aims to estimate the energy consumed by different 5G base stations, taking into account various engineering configurations, traffic conditions, and energy-saving methods.

## Problem Statement

Network operational expenditure (OPEX) accounts for approximately 25% of a telecom operator’s total costs, with 90% of this being spent on energy bills. More than 70% of the energy consumed is estimated to be by the radio access network (RAN), particularly the base stations (BSs). The objective of this project is to build and train machine learning models to estimate energy consumption accurately.

## Dataset Description

The dataset includes the following columns:

- **Time:** Timestamp of the record
- **BS:** Base Station identifier
- **Energy:** Energy consumption (target variable)
- **load:** Network load
- **ESMODE:** Energy-saving mode status
- **TXpower:** Transmission power

### Data Preprocessing

1. **Dropped Columns:** The `Time` and `BS` columns were dropped as they do not directly contribute to predicting energy consumption.
2. **Target Variable:** The `Energy` column was chosen as the target variable.
3. **Correlation Analysis:** 
   - The correlation matrix revealed the following relationships:

   | Variable | Energy  | load     | ESMODE   | TXpower  |
   |----------|---------|----------|----------|----------|
   | Energy   | 1.000   | 0.643    | -0.271   | 0.451    |
   | load     | 0.643   | 1.000    | -0.208   | 0.200    |
   | ESMODE   | -0.271  | -0.208   | 1.000    | 0.060    |
   | TXpower  | 0.451   | 0.200    | 0.060    | 1.000    |

   - The `ESMODE` variable was dropped due to its negative correlation with energy consumption.

## Machine Learning Models

Two machine learning models were evaluated:

1. **Linear Regression**
2. **XGBoost Regression**

### Model Performance

- **Best Performing Model:** XGBoost Regression
- **Metrics:**
  - **Mean Squared Error (MSE):** 76.40
  - **R-squared (R²):** 0.51
  - **Mean Absolute Error (MAE):** 6.62

## Conclusion
This project demonstrates the application of machine learning techniques in predicting energy consumption for 5G base stations. The results obtained from the XGBoost regression model indicate a promising approach to addressing energy management challenges in telecommunications.

## Acknowledgements
Thank you to the International Telecommunication Union (ITU) for organizing this challenge and providing the dataset.
