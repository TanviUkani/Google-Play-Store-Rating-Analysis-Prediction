# Google Play Store App Rating Analysis and Prediction

## Project Overview

This project analyzes Google Play Store applications and builds machine learning models to predict app ratings based on available app characteristics.

The project follows a complete machine learning workflow including data cleaning, feature engineering, exploratory data analysis (EDA), model building, evaluation, and interpretation of results.

---

## Project Goal

To analyze Google Play Store app data, identify factors associated with app ratings, and develop machine learning models to predict app ratings using available app features.

---

## Dataset

Google Play Store Apps Dataset

### Features Used

- Category
- Reviews
- Size
- Installs
- Type
- Price
- Content Rating
- Year Updated
- Month Updated
- Size Varies

### Target Variable

- Rating

---

## Data Cleaning

The following preprocessing steps were performed:

- Removed duplicate records
- Removed an anomalous record containing an invalid rating value (19.0)
- Handled missing values
- Converted Reviews to numeric format
- Cleaned and standardized Size values
- Cleaned Installs column
- Cleaned Price column
- Extracted Year Updated and Month Updated from Last Updated
- Created Size Varies indicator feature

---

## Feature Engineering

### Features Created

- Year Updated
- Month Updated
- Size Varies

### Transformations Applied

- Log transformation on:
  - Reviews
  - Installs
  - Size
  - Price

### Encoding

One-Hot Encoding:

- Category
- Type
- Content Rating

### Scaling

StandardScaler was applied to numerical features before training Linear Regression.

---

## Exploratory Data Analysis (EDA)

The analysis included:

- Rating distribution analysis
- Category-wise rating analysis
- Content Rating analysis
- Type-wise analysis
- Correlation analysis
- Feature relationship visualization
- Outlier identification

### Key EDA Findings

- Most app ratings are concentrated between 4.0 and 4.5.
- Family category contains the highest number of apps.
- Categories such as Events and Art & Design showed high average ratings despite having fewer apps.
- Most numerical features showed weak correlation with app ratings.
- More installs or reviews do not necessarily guarantee higher ratings.

---

## Machine Learning Models

### 1. Linear Regression

Linear Regression was used as the baseline model.

**Results**

- Test R² Score: 0.037

### 2. Random Forest Regressor

A Random Forest model was trained to capture non-linear relationships.

**Results**

- Train R² Score: 0.878
- Test R² Score: 0.088

The large gap between training and testing performance indicated significant overfitting.

### 3. Tuned Random Forest Regressor

Hyperparameter tuning was performed to improve generalization.

Parameters used:

RandomForestRegressor(
    n_estimators=300,
    max_depth=8,
    min_samples_split=20,
    min_samples_leaf=10,
    random_state=42
)

**Results**

- Train R² Score: 0.220
- Test R² Score: 0.124

This model achieved the best balance between learning and generalization.

---

## Feature Importance

Top contributing features identified by the tuned Random Forest model:

1. Reviews
2. Size
3. Month Updated
4. Installs
5. Year Updated
6. Price

These features contributed the most to the model's predictions.

---

## Key Findings

- Linear relationships between available features and ratings are weak.
- Random Forest outperformed Linear Regression.
- Hyperparameter tuning reduced overfitting and improved test performance.
- Reviews and Size were among the most influential features.
- The available dataset contains limited predictive signal for accurately predicting app ratings.

---

## Conclusion

The final tuned Random Forest model achieved a Test R² score of approximately 0.12, outperforming the baseline Linear Regression model.

Although predictive performance remains limited, the project demonstrates a complete machine learning workflow and highlights an important real-world insight:

**Model performance is heavily dependent on data quality and feature availability. Many factors that influence app ratings, such as user experience, app design, performance, and customer satisfaction, are not present in the dataset.**

---

## Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn

---

## Repository Structure

```text
├── Google_Play_Store_Rating_Analysis_and_Prediction.ipynb
├── README.md
```

---

## Author

Tanvi Ukani
