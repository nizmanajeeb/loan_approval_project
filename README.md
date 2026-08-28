# Financial Decision Support System for Loan Approval

## 1. Problem Statement
Financial organizations receive loan applications from individuals with different demographic, employment, and financial characteristics. This project analyzes historical applicant information and develops a machine-learning-based decision-support system to predict whether a loan application is likely to be approved.

The project also considers prediction errors because false approvals and false rejections can have different financial consequences.

## 2. Objectives
1. Understand the loan applicant data.
2. Identify the historical loan approval outcome.
3. Assess data quality.
4. Perform appropriate cleaning and preprocessing.
5. Investigate meaningful patterns and relationships.
6. Prepare features for machine learning.
7. Develop and compare two classification approaches.
8. Evaluate the models using suitable metrics.
9. Examine false-positive and false-negative predictions.
10. Select and justify a final model.
11. Discuss limitations and possible improvements.

## 3. Dataset Description
The Loan Approval Dataset contains 1,000 applicants and 11 variables.

| Column | Description |
|---|---|
| `applicant_id` | Unique applicant identifier |
| `age` | Applicant age |
| `gender` | Applicant gender |
| `marital_status` | Marital status |
| `annual_income` | Annual income |
| `loan_amount` | Requested loan amount |
| `credit_score` | Applicant credit score |
| `num_dependents` | Number of dependents |
| `existing_loans_count` | Number of existing loans |
| `employment_status` | Employment category |
| `loan_approved` | Historical loan approval outcome |

The target is `loan_approved`: `1` = approved and `0` = rejected. `applicant_id` is an identifier and is not used as a predictive feature.

## 4. Approach
The project follows this workflow:

1. Load and inspect the dataset.
2. Check dimensions, columns, data types, missing values and duplicates.
3. Calculate descriptive statistics.
4. Investigate distributions and possible outliers.
5. Explore relationships with loan approval.
6. Examine numerical correlations.
7. Prepare features and target.
8. Split data into training and testing sets.
9. Encode categorical variables.
10. Standardize numerical variables where appropriate.
11. Train Decision Tree and KNN classifiers.
12. Evaluate and compare the models.
13. Examine confusion matrices and prediction errors.
14. Select the preferred model.

## 5. Data Cleaning and Preprocessing
The dataset was checked for missing values, duplicates, data types and unusual numerical values. No missing-value imputation was required because the dataset contained no missing values.

Potential outliers were considered rather than automatically removed because extreme financial values may represent genuine applicants.

For modelling, `applicant_id` was excluded, `loan_approved` was used as the target, categorical variables were one-hot encoded, and numerical variables were standardized using `StandardScaler`. An 80/20 stratified train-test split with `random_state=42` was used.

## 6. Exploratory Data Analysis
The notebook investigates loan-approval distribution, age, income, loan amount, credit score, potential outliers, credit score versus approval, income versus approval, employment status versus approval, existing loans versus approval, and correlations among numerical variables.

The analysis identified meaningful relationships between credit score, income, employment status, existing loans and historical approval outcomes.

## 7. Machine Learning Models

### Decision Tree
A Decision Tree was selected because it is a suitable classification method and provides an interpretable rule-based structure.

### K-Nearest Neighbors (KNN)
KNN was selected as a second classification approach. It predicts based on nearby observations and provides a useful contrast with the tree-based model.

## 8. Evaluation Measures
The models were evaluated using accuracy, precision, recall, F1-score and confusion matrices.

Accuracy measures overall correctness. Precision measures the correctness of positive predictions. Recall measures how many actual positive cases are identified. F1-score balances precision and recall. The confusion matrix shows the different types of prediction errors.

## 9. Results

| Model | Accuracy | Precision | Recall | F1-score |
|---|---:|---:|---:|---:|
| Decision Tree | 99.00% | 98.65% | 100.00% | 99.32% |
| KNN | 86.50% | 86.96% | 95.89% | 91.21% |

### Confusion matrices

Decision Tree:
```text
[[52, 2],
 [0, 146]]
```

KNN:
```text
[[33, 21],
 [6, 140]]
```

The Decision Tree produced fewer false-positive and false-negative predictions on the test set.

## 10. Final Model
The Decision Tree is selected as the preferred model because it achieved higher accuracy, precision, recall and F1-score than KNN and produced fewer prediction errors on the test set.

Its exceptionally high test performance should nevertheless be interpreted cautiously because an unrestricted Decision Tree can potentially overfit. Further validation and tree-depth tuning would be useful before real-world deployment.

## 11. Major Decisions and Reasoning
- **Dataset:** It contains applicant information and a historical approval outcome, making it suitable for supervised binary classification.
- **Missing values:** No imputation was needed because there were no missing values.
- **Outliers:** They were not automatically removed because extreme financial values may be legitimate.
- **Scaling:** Standardization is especially important for KNN because it uses distances.
- **Encoding:** One-hot encoding converts categorical variables into suitable numerical representations.
- **Models:** Decision Tree and KNN provide two different classification approaches.
- **Evaluation:** Multiple metrics and confusion matrices were used because different prediction errors can have different consequences.

## 12. Limitations
1. The dataset contains only 1,000 records.
2. It may not represent all real-world loan applicants.
3. The historical outcome may reflect assumptions in the dataset.
4. Evaluation is based on a single train/test split.
5. The very high Decision Tree performance should be validated further.
6. The model is a decision-support exercise, not an automatic real-world loan approval system.

## 13. Future Improvements
- Use cross-validation.
- Tune Decision Tree depth and other parameters.
- Test additional suitable classifiers if permitted.
- Use a larger and more representative dataset.
- Investigate fairness and potential bias.
- Monitor performance on new applicant data.

## 14. Project Files
- `loan_approval.ipynb` – analysis and machine-learning notebook
- `loanapproval.csv` – dataset
- `research_notes.md` – research notes

## 15. Conclusion
This project demonstrates how historical loan application data can be explored and used to build a data-driven decision-support model. Two classification approaches, Decision Tree and KNN, were developed and compared. For this dataset and test split, the Decision Tree performed substantially better and was selected as the final model, while recognizing that further validation would be required before real-world use.
