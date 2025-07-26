# Course: MSCS 634 – Advanced Data Mining for Data-Driven Insights and Predictive Modeling

## Deliverable 2: Regression Modeling and Performance Evaluation

## Objective
The objective of this lab was to develop and evaluate regression models to predict the number of hours worked per week by individuals using demographic and socio-economic features from the Adult Income dataset. The lab involved:

- Feature engineering and preprocessing
- Model training using Linear, Ridge, and Lasso regression
- Evaluation using R², MSE, and RMSE
- Cross-validation to assess generalizability
- Visual diagnostics (scatter plots, residuals)

---

## Dataset Summary
- **Source**: UCI Adult Income Dataset
- **Size**: 18,983 records after cleaning (originally 40,000+ records), 15 features
- **Target Variable**: `hours-per-week` (continuous)
- **Features**: A mix of categorical (e.g., education, workclass, occupation) and numerical (e.g., age, capital-gain) attributes

---

## Data Preparation and Feature Engineering
- Used `OneHotEncoder` for categorical features and `StandardScaler` for numerical features.
- Applied a `ColumnTransformer` to streamline preprocessing within a `Pipeline`.
- Split data into training and test sets for evaluation, and used the entire dataset for cross-validation and visualization.

---

## Models Trained
1. **Linear Regression**
2. **Ridge Regression** (α = 1.0)
3. **Lasso Regression** (α = 0.1)

All models were implemented using scikit-learn pipelines with preprocessing and training steps combined.

---

## Evaluation Metrics

| Model              | Test R² | CV R²   | Test RMSE | CV RMSE | Test MSE | CV MSE  |
|--------------------|---------|---------|-----------|---------|----------|---------|
| Linear Regression  | 0.1057  | 0.0997  | 3.7628    | 3.7472  | 14.1585  | 14.0446 |
| Ridge Regression   | 0.1061  | 0.1001  | 3.7620    | 3.7464  | 14.1523  | 14.0386 |
| Lasso Regression   | 0.0574  | 0.0600  | 3.8631    | 3.8290  | 14.9234  | 14.6646 |

where CV = Cross-Validated

## Visualizations Included
- **Bar charts** comparing test and CV metrics (R², MSE, RMSE)
- **Actual vs. Predicted scatter plots** for each model
- **Residual plots** to analyze error patterns

---

## Insights & Observations
- Ridge Regression showed the most consistent performance between test and cross-validation, with the lowest RMSE and highest R².
- Linear Regression followed closely and served as a reliable baseline model.
- Lasso Regression underperformed, likely due to overly aggressive feature penalization (L1 regularization).
- Residual plots showed funnel-shaped variance and horizontal banding, suggesting difficulty modeling exact work hour levels (e.g., 40-hour clusters).
- All models had relatively low R² scores (< 0.11), indicating that the features explain only a small portion of the variance in work hours — likely due to unmeasured behavioral or occupational factors.

---

## Challenges Encountered
- Target variable (`hours-per-week`) was heavily concentrated around common work norms (e.g., 40 hours), limiting variance.
- Lasso regression penalized important features and led to underfitting.
- Capturing behavioral data through linear models may have limited predictive capacity.

---

## Outcome
The Ridge Regression model was identified as the most reliable and stable. While all models were limited in accuracy due to the dataset’s nature, the lab provided strong experience in regression evaluation, model comparison, and diagnostic plotting.

---

## Files Included
- `project_deliverable_2.ipynb`: Complete notebook with code, visualizations, and commentary
- `adult_income_cleaned.csv`: Cleaned dataset obtained from Deliverable 1 used for modeling
- `README.md`: Summary and interpretation of lab deliverable