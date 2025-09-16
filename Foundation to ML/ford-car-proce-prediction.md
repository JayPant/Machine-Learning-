# Ford Cars Price Prediction 

Summary
- Regression analysis to predict used Ford car prices from the provided `ford.csv` dataset.
- Two preprocessing/encoding strategies were compared:
    - One-hot encoding (X_one_encode) + StandardScaler for numerical features.
    - Label encoding (X_label) + StandardScaler for all features.
- Linear Regression models were trained and evaluated (train/test split with `random_state=42`, `test_size=0.33`).

Files / Inputs
- `ford.csv` — source dataset loaded in the notebook (cell 1).
- This notebook — performs EDA, preprocessing, model training and evaluation.

Environment / Dependencies
- Python 3.x
- numpy
- pandas
- scikit-learn
- seaborn
- matplotlib

Quick Notes on Notebook Structure
- Cells 0–6: imports, data loading, basic inspection (head, shape, info, describe, null checks).
- Cells 7–15: EDA using seaborn/matplotlib (histogram, heatmap, boxplots, scatterplots).
- Cells 16–19: Feature/target split and one-hot encoding pipeline (X_one_encode).
- Cells 20–26: Label encoding pipeline (X_label) and scaling.
- Cells 27–35: Train/test split and LinearRegression using X_one_encode; predictions and R² / adjusted R² calculation.
- Cells 36–42: Train/test split and LinearRegression using X_label; predictions and R² / adjusted R² calculation.

Preprocessing Details
- Target: `price` (column in the original dataframe `df`).
- Categorical columns encoded:
    - One-hot: `model`, `transmission`, `fuelType` (drop_first=True).
    - Label: `model`, `transmission`, `fuelType` (LabelEncoder).
- Numerical features scaled with `StandardScaler`: `year`, `mileage`, `tax`, `mpg`, `engineSize`.
- Train/test split: `test_size=0.33`, `random_state=42`.

Modeling & Results
- Model type: Linear Regression (scikit-learn).
- Final evaluation metrics (from the notebook run):
    - R² ≈ 0.7310
    - Adjusted R² ≈ 0.7307
- Interpretation: The linear model explains about 73% of the variance in price on the test set. Consider non-linear models or more feature engineering for further improvement.

How to Reproduce
1. Ensure dependencies are installed (pip install pandas numpy scikit-learn seaborn matplotlib).
2. Place `ford.csv` in the working directory.
3. Run the notebook cells in order. Key steps:
     - Load data (cell 1).
     - Perform EDA (cells 7–15).
     - Build preprocessing pipelines: one-hot (cells 18–23) and label (cells 20–26).
     - Train/evaluate LinearRegression for each processed X (cells 28–35 and 36–42).

Suggested Next Steps
- Try tree-based models (RandomForest, XGBoost) and compare metrics.
- Perform cross-validation instead of a single train/test split.
- Add feature engineering (age from year, log-transform mileage, interaction terms).
- Evaluate residuals and check assumptions (linearity, homoscedasticity).
- Save best model with joblib/pickle and create a small prediction API.

Contact / Attribution
- Notebook authored for exploratory model-building and baseline evaluation of used car price prediction.