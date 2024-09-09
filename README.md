# Bureau_Assignment
# Model Approach and Results

## Approach Used in the Code

### 1. Data Preparation

#### Data Loading
- The training and test datasets are loaded from CSV files into pandas DataFrames.

#### Handling Missing Values
- Missing values in both train and test datasets are filled using the mode of the respective columns.

#### Feature Engineering
- Date features from the 'APPLICATION LOGIN DATE' are extracted, including month, day, and day of the week.
- The 'Cibil Score' column is converted to numeric, with non-numeric values coerced to NaN.

#### Feature Selection
- Features are categorized into numeric, categorical, and boolean types. This classification helps in applying appropriate preprocessing methods.

### 2. Data Splitting
- The data is split into training and validation sets using an 80-20 split ratio.

### 3. Preprocessing Pipelines

#### Numeric Features
- Imputation with median values for missing data.
- Standardization using `StandardScaler`.

#### Categorical Features
- Imputation with a constant value of 'missing'.
- One-hot encoding using `OneHotEncoder`.

#### Boolean Features
- Imputation with a constant value of 0.

#### ColumnTransformer
- Combines the above preprocessing steps for different feature types.

### 4. Model Building and Evaluation

#### Pipeline Creation
- A pipeline is created combining the preprocessing steps with a `RandomForestClassifier`.

#### Grid Search
- `GridSearchCV` is used for hyperparameter tuning to find the best model parameters.

#### Model Evaluation
- The best model is evaluated on the validation set using classification metrics like precision, recall, F1-score, and ROC AUC score.
- A confusion matrix is plotted to visualize the performance.

#### Feature Importance
- Feature importances are extracted from the model and visualized using a bar plot to identify the most influential features.

#### Test Set Predictions
- Predictions are made on the test set and saved to a CSV file for submission.

## Predicted Results Insights

### Classification Report
| Class     | Precision | Recall | F1-Score | Support |
|-----------|-----------|--------|----------|---------|
| APPROVED  | 0.87      | 0.94   | 0.90     | 1327    |
| DECLINED  | 0.85      | 0.74   | 0.79     | 673     |
| **Accuracy**  |           |        | 0.87     | 2000    |
| **Macro Avg** | 0.86      | 0.84   | 0.85     | 2000    |
| **Weighted Avg** | 0.87      | 0.87   | 0.87     | 2000    |

### Confusion Matrix
- The confusion matrix indicates how well the model performs in classifying the two target classes:
  - **True Positives (TP)**: Number of correctly predicted 'APPROVED' cases.
  - **True Negatives (TN)**: Number of correctly predicted 'DECLINED' cases.
  - **False Positives (FP)**: Number of 'DECLINED' cases incorrectly predicted as 'APPROVED'.
  - **False Negatives (FN)**: Number of 'APPROVED' cases incorrectly predicted as 'DECLINED'.

### Feature Importance
- The top 10 most important features according to the RandomForestClassifier are visualized to understand which features have the most influence on the model's predictions.

## Conclusion

### Model Performance
- The model performs well with an overall accuracy of 87%.
- It shows strong precision and recall for the 'APPROVED' class, indicating reliable predictions for this class.
- The 'DECLINED' class has slightly lower performance metrics, particularly in recall, suggesting room for improvement in identifying 'DECLINED' cases.

### Feature Insights
- The feature importance plot provides insights into which features contribute most to the model's predictions. This can be useful for understanding the factors driving the decisions.

### Next Steps
- Investigate further to understand why the model struggles with 'DECLINED' predictions and consider additional feature engineering or model tuning.
- Validate the model's predictions on new data and ensure that it generalizes well to unseen cases.
