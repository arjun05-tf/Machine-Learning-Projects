TITANIC SURVIVAL PREDICTION
In this project, I built an end-to-end Machine Learning pipeline to predict passanger survival on the Titanic.
Note: This project doesn't demonstrate hyperparameter tuning or any kind of optimization but rather focuses on creating different pipeline for Numerical and Categorical data with appropriate parameters and estimators and then combining them in the end.

Problem
Binary Classification Task:
-Target: Survived (0 = did not survive, 1 = survive)
-Data: Kaggle Titanic dataset (891 samples) # The goal was to build a pipeline so data does not play much role here, it is just for the metrics and final evaluation but that is irrelevant to the project goal.

Approach
1) Data Handling:
-Selected numeric and categorical features only
-Dropped identifier and high-cardinality columns (PassengerId, Name, Ticket, Cabin)

2) Data Splitting:
-Train: 60%
-Validation (CV): 20%
-Test: 20%
Stratified splits to preserve class balance
-Test set is not touched until final pipeline is ready

3) Preprocessing
All preprocessing was done using scikit-learn Pipelines and ColumnTransformer to prevent data leakage.
-Numeric features: mean imputation + standard scaling
-Categorical features: most-frequent imputation + one-hot encoding

Note: Nothing is implemented from scratch, libraries and necessary features were used directly. Goal is to understand pipeline, not the working behind it.
Preprocesing statistics were learned only from training data and reused for validation and test sets.

Baseline
A majority-class baseline model was used as a sanity check.
-Baseline accuracy: ~62%

Models Trained
1) Logistic Regression
- Implemented as part of a full preprocessing + model pipeline
- Validation accuracy: ~81%

2) Random Forest
- Same preprocessing pipeline
- Validation accuracy: ~81%

The more complex model (Random Forest) did not outperform Logistic Regression.

Evaluation
Models were evaluated on the validation set using:
- Accuracy
- Precision
- Recall
- F1-score
- Confusion matrix

An improvement attmempt using class_weight = "balanced" in logistic regression was tested but was later discarded due to overall reduced performance.

Final Model
Logistic Regression (no class weight) was selected based on:
- Best overall validation performance
- Simplicity and interpretability
- Comparable performance to Random Forest

Final Test Results
The final model was retrained on train + validation data and evaluated once on the test set.
- Test accuracy: ~81%
Test performance closely mathced validation performance, indicating good generalization.

Key Learnings:
- Data leakage commonly occurs during preprocessing, not modeling
- Pipeline enforces a clean separation between learning preprocessing rules and applying them
- Baseline models are essential for meaningful evaluation
- More complex models do not always perform better on small tabular datasets
- Workflow correctness matters more than small metric gains.

How to Run
Run the notebook file.ipynb top-to-bottom.
All steps are fully reproducible

Author
Arjun Vinod Patil
