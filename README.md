
# Predicting Apartment Prices in Mexico City
Regression-based modeling and analysis of real estate prices in Mexico City.

This project focuses on building a machine learning model to predict apartment prices in Mexico City using real estate data.

## Project Goal
The primary goal is to develop a predictive model that can estimate the price of an apartment in Mexico City based on various features such as area, location, and other property characteristics. This can be useful for buyers, sellers, and real estate agents to get a fair market value assessment.

## Data
The data used in this project is sourced from several CSV files named `mexico-city-real-estate-*.csv`. Each file contains information about apartment listings, including price, location, surface area, and other relevant details.

## Methodology

### 1. Data Preparation (`wrangle` function)
The data preparation phase involved several steps to clean and transform the raw data into a suitable format for modeling:
*   **Filtering**: Apartments were filtered to include only those in "Distrito Federal" with prices less than $100,000 USD and classified as "apartment" type.
*   **Outlier Removal**: Outliers in `surface_covered_in_m2` were removed by keeping values between the 10th and 90th percentiles.
*   **Feature Engineering**:
    *   The `lat-lon` column was split into separate `lat` and `lon` columns.
    *   The `borough` was extracted from `place_with_parent_names`.
*   **Column Dropping**:
    *   Columns with high numbers of null values (`floor`, `expenses`) were dropped.
    *   Low- and high-cardinality categorical variables (`operation`, `property_type`, `currency`, `properati_url`) were removed.
    *   Leaky columns (direct price indicators like `price`, `price_aprox_local_currency`, `price_per_m2`, `price_usd_per_m2`) were excluded to prevent data leakage.
    *   Columns exhibiting multicollinearity (`surface_total_in_m2`, `rooms`) were also dropped.

### 2. Baseline Model
A simple baseline model was established by predicting the mean of the target variable (`price_aprox_usd`). The Mean Absolute Error (MAE) for this baseline was calculated to serve as a reference point for evaluating the performance of the machine learning model.

### 3. Machine Learning Model
A pipeline was constructed for the machine learning model:
*   **OneHotEncoder**: Categorical features were converted into a numerical format using One-Hot Encoding.
*   **SimpleImputer**: Missing numerical values were imputed with the mean of their respective columns.
*   **Ridge Regressor**: A Ridge Regression model was used for prediction, which is a linear model with L2 regularization to prevent overfitting.

## Results
The model was trained on the prepared data to predict apartment prices. Feature importances were analyzed to understand which features have the most significant impact on the predicted price.

## How to Run
1.  Clone this repository.
2.  Install the required libraries (e.g., `pandas`, `scikit-learn`, `category-encoders`, `matplotlib`, `seaborn`, `plotly`).
3.  Run the Jupyter Notebook or Python script that contains the data loading, wrangling, model training, and prediction steps.

## Dependencies
*   `pandas`
*   `numpy`
*   `scikit-learn`
*   `category-encoders`
*   `matplotlib`
*   `seaborn`
*   `plotly`
