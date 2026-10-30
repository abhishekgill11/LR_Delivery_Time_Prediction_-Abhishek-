# Delivery Time Prediction using Machine Learning

## Project Overview

This project focuses on predicting food delivery time using historical order and operational data from a logistics platform.

The objective is to understand the factors influencing delivery time, develop a predictive model using Machine Learning, and identify operational patterns that could help improve delivery efficiency.

The project follows an end-to-end Machine Learning workflow, covering data preprocessing, exploratory data analysis, feature engineering, feature selection, model development, and evaluation.

## Business Problem

Accurate delivery-time estimation is important for customer satisfaction and efficient logistics operations.

Delivery delays can be influenced by several factors, including:

* Distance between the restaurant and customer.
* Order size and complexity.
* Availability of delivery personnel.
* Number of outstanding orders.
* Time and day of order placement.

This project investigates these factors and develops a Linear Regression model to estimate delivery time.

## Dataset Overview

The dataset contains approximately **175,777 delivery records** with order-level and operational information.

Key features include:

| Feature                    | Description                  |
| -------------------------- | ---------------------------- |
| `market_id`                | Market identifier            |
| `store_primary_category`   | Restaurant category          |
| `order_protocol`           | Order placement protocol     |
| `total_items`              | Total items in an order      |
| `subtotal`                 | Order subtotal               |
| `num_distinct_items`       | Number of distinct items     |
| `total_onshift_dashers`    | Available delivery personnel |
| `total_busy_dashers`       | Busy delivery personnel      |
| `total_outstanding_orders` | Outstanding orders           |
| `distance`                 | Delivery distance            |
| `order_hour`               | Hour of order placement      |
| `order_day`                | Day of order placement       |

**Target Variable:** `delivery_time` (minutes), calculated using the difference between actual delivery time and order creation time.

## Tech Stack

* **Programming:** Python
* **Data Manipulation:** Pandas, NumPy
* **Visualization:** Matplotlib, Seaborn
* **Machine Learning:** Scikit-learn
* **Model:** Linear Regression
* **Feature Selection:** Recursive Feature Elimination (RFE)

## Project Workflow

### 1. Data Cleaning and Preprocessing

* Inspected dataset structure, data types, and missing values.
* Converted datetime columns and created delivery-time features.
* Investigated negative and zero values in operational variables.
* Prepared numerical and categorical features for modelling.

### 2. Exploratory Data Analysis (EDA)

* Performed univariate and bivariate analysis.
* Examined distributions of numerical and categorical variables.
* Used boxplots to identify potential outliers.
* Analysed correlations between delivery time and operational features.

### 3. Outlier and Data Quality Analysis

* Applied the Interquartile Range (IQR) method to identify potential outliers.
* Identified 16,678 potential outliers (11.86%) in `num_distinct_items`.
* Investigated unusual negative and zero values rather than automatically removing all statistical outliers.

### 4. Feature Engineering and Selection

* Extracted order hour and day from order timestamps.
* Created a weekend indicator.
* Applied feature scaling.
* Used Recursive Feature Elimination (RFE) to evaluate different feature subsets.
* Retained all 15 features based on the lowest validation RMSE.

### 5. Model Development and Evaluation

* Split the dataset into training and testing sets.
* Developed a Linear Regression model.
* Evaluated performance using RMSE and R².
* Conducted residual and coefficient analysis to understand model behaviour.

## Model Performance

The Linear Regression model achieved the following results:

| Evaluation Metric        |       Result |
| ------------------------ | -----------: |
| Test RMSE                | 3.22 minutes |
| Test R²                  |       0.8813 |
| Best RFE Validation RMSE | 3.19 minutes |
| Selected Features        |           15 |

The model explained approximately **88.13% of the variation** in delivery time on the held-out test dataset.

## Key Findings

* Delivery distance showed a positive correlation of approximately 0.46 with delivery time.
* Order subtotal showed a positive correlation of approximately 0.41.
* Total outstanding orders showed a positive correlation of approximately 0.39.
* Order hour showed a negative correlation of approximately -0.35.
* Residual analysis indicated patterns in prediction errors, suggesting opportunities for further model improvement.

## Business Recommendations

Based on the analysis, potential operational improvements include:

1. Investigating route allocation for longer-distance deliveries.
2. Monitoring outstanding orders to identify periods of operational congestion.
3. Evaluating delivery capacity during high-demand hours.
4. Investigating preparation delays associated with complex orders.
5. Using predicted delivery times to identify orders potentially at risk of delay.

These recommendations require further operational validation; the analysis identifies associations rather than proving causation.

## Limitations and Future Improvements

* Explore appropriate categorical encoding and preprocessing pipelines.
* Compare Linear Regression with Decision Tree, Random Forest, and Gradient Boosting models.
* Apply cross-validation for more robust performance evaluation.
* Investigate heteroscedasticity and other residual patterns.
* Explore hyperparameter tuning and additional feature engineering.
* Separate restaurant preparation time from delivery travel time where additional timestamps are available.

## Conclusion

This project demonstrates an end-to-end Machine Learning workflow for delivery-time prediction. It combines exploratory analysis, data-quality investigation, feature selection, predictive modelling, and business interpretation.

The project also establishes a foundation for exploring more advanced Machine Learning techniques and improving operational decision-making.

---

**Author:** Abhishek
**Focus:** Machine Learning | Predictive Analytics | Python | Data Analysis
