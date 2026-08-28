# Research Notes

## 1. Exploratory Data Analysis (EDA)

### What I needed to understand
How to investigate a dataset before building a machine-learning model and identify useful patterns.

### What I researched
Descriptive statistics, distributions, boxplots, group comparisons and correlation analysis.

### What I learned
EDA helps understand data structure and quality. Statistics describe variables, while visualizations can reveal distributions, outliers and relationships.

### How I applied it
I inspected the dataset, calculated descriptive statistics, plotted numerical distributions, used boxplots for potential outliers and compared applicant characteristics with loan approval.

---

## 2. One-Hot Encoding

### What I needed to understand
How categorical variables such as gender, marital status and employment status can be used by machine-learning models.

### What I researched
One-hot encoding and categorical-variable preprocessing.

### What I learned
One-hot encoding represents categories using separate binary indicator variables without implying a numerical order.

### How I applied it
I used `OneHotEncoder` in the preprocessing pipeline for categorical applicant variables.

---

## 3. Feature Scaling and Standardization

### What I needed to understand
Why numerical variables with different ranges may need scaling.

### What I researched
Standardization and its importance for distance-based algorithms.

### What I learned
Standardization puts numerical variables on a comparable scale. This is particularly important for KNN because it uses distances between observations.

### How I applied it
I used `StandardScaler` in the preprocessing pipeline.

---

## 4. K-Nearest Neighbors (KNN)

### What I needed to understand
How KNN can classify loan applications.

### What I researched
Nearest neighbours, distance-based classification and the importance of feature scaling.

### What I learned
KNN predicts a class using nearby observations. The scale of features can affect the calculated distances.

### How I applied it
I implemented `KNeighborsClassifier` after preprocessing the numerical and categorical features.

---

## 5. Decision Tree Classification

### What I needed to understand
How a Decision Tree classifies loan applications.

### What I researched
Decision nodes, splitting, leaf nodes, classification and overfitting.

### What I learned
A Decision Tree repeatedly splits data using feature conditions. A very complex tree can overfit the training data.

### How I applied it
I trained a `DecisionTreeClassifier` and evaluated it on the test set.

---

## 6. Train-Test Split and Reproducibility

### What I needed to understand
How to evaluate models on data that was not used during training.

### What I researched
Training/testing sets, stratification and `random_state`.

### What I learned
The training set is used to learn the model, while the test set estimates performance on unseen data. A fixed random state makes the split reproducible.

### How I applied it
I used an 80/20 stratified split with `random_state=42`.

---

## 7. Classification Evaluation Metrics

### What I needed to understand
Why accuracy alone is not enough to compare financial classification models.

### What I researched
Accuracy, precision, recall and F1-score.

### What I learned
- Accuracy measures overall correctness.
- Precision measures the correctness of positive predictions.
- Recall measures how many actual positive cases are detected.
- F1-score balances precision and recall.

### How I applied it
I calculated all four metrics for Decision Tree and KNN and compared them.

---

## 8. Confusion Matrix and Prediction Errors

### What I needed to understand
How false positives and false negatives should be interpreted.

### What I researched
True positives, true negatives, false positives and false negatives.

### What I learned
A confusion matrix shows both correct predictions and the types of mistakes made by a classifier.

For this project:
- A false positive is a case predicted as approved when the historical outcome is rejection.
- A false negative is a case predicted as rejected when the historical outcome is approval.

These errors can have different implications, so accuracy alone is not sufficient.

### How I applied it
I generated confusion matrices for both models and compared their error counts.

---

## 9. Model Comparison and Selection

### What I needed to understand
How to select the more suitable model from Decision Tree and KNN.

### What I researched
Comparing classification models using multiple metrics and confusion matrices.

### What I learned
Model selection should consider overall performance, error types and the context of the problem rather than a single metric.

### How I applied it
The Decision Tree achieved:

- Accuracy: 99.00%
- Precision: 98.65%
- Recall: 100.00%
- F1-score: 99.32%

KNN achieved:

- Accuracy: 86.50%
- Precision: 86.96%
- Recall: 95.89%
- F1-score: 91.21%

The Decision Tree also produced fewer prediction errors on the test set, so it was selected as the final model.

---

## 10. Reflection

The main lesson from the project was that machine learning is not only about training a model. The data must first be understood and cleaned, relationships should be investigated, preprocessing choices should be justified, and model errors must be interpreted in the context of the problem.

I also learned that comparing multiple evaluation measures gives a more complete understanding of model performance than using accuracy alone.
