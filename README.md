Part 2: Supervised Machine Learning – Build, Train and Evaluate

The goal of this project is to construct supervised machine learning models from the cleaned insurance dataset. Two prediction tasks were executed.

1) Using Linear and Ridge Regressions to Predict
2) Using Logistic Regression for Binary Classification

The evaluation and tracking of the models was accomplished with many metrics.

Dataset
Dataset: Medical Insurance Cost Dataset
Rows: 1337
Columns: 7
Regression Target: charges
Classification Target: charges > median(charges)

Feature Engineering
The feature matrix contains:
1) age
2) sex
3) bmi
4) children
5) smoker
6) region
The regression target is charges
The binary classification target was created using python
y_clf = (charges > charges.median()).astype(int)
where,
0 = Low Insurance Charges
1 = High Insurance Charges

Data Preprocessing
Categorical variables:
1) sex
2) smoker
3) region
were converted using One-Hot Encoding.

Train-Test Split
The dataset was divided into
1) 80% Training
2) 20% Testing

Feature Scaling
StandardScaler fit the training data only.The same data scaler was used to transform the test data. Since the statistics from the test set are not applied during training, none can leak.

Regression Models
A) Linear Regression
The scaled training data was used to train the Linear Regression model.
Evaluation Metrics
1) Mean Squared Error (MSE)
2) R² Score
Analyzing coefficients allows us to determine the most impactful features.
B) Ridge Regression
Ridge Regression was trained with
alpha = 1.0
The model was put to the test against Linear Regression.
1) MSE
2) R² Score
Ridge regression uses L2 regularization to constrain coefficient size to decrease overfitting and variance.

Classification Model
The model was trained with the Logistic Regression algorithm, with the parameter “max_iter” set to 1000. Because the classes created using the median were balanced, no further imbalance handling measures were required. 
The following evaluation metrics were computed:
1) Confusion Matrix
2) Accuracy
3) Precision
4) Recall
5) F1 Score
6) ROC Curve
7) AUC

Precision = TP / (TP + FP)
Recall = TP / (TP + FN)

ROC Curve
The ROC Curve shows the association between the True Positive Rate and False Positive Rate at various thresholds. While the AUC refers to the area under the ROC Curve, a better AUC indicates the better classification of the model.
Decision Threshold Analysis

The Logistic Regression probabilities were evaluated using the following thresholds:
1) 0.30
2) 0.40
3) 0.50
4) 0.60
5) 0.70
Precision, Recall and F1-score were calculated for every threshold.The threshold with the highest F1-score was identified.

Regularization Experiment
A second Logistic Regression model was trained using C = 0.01

The following metrics were compared with the baseline model:
1) Precision
2) Recall
3) AUC
The parameter C controls the strength of regularization.
The lower the value of C increases regulation.

Files Included
1) cleaned_data.csv
2) part2.ipynb
3) README.md
4) requirements.txt
5) roc_curve.png

The regression and classification models were trained successfully on the cleaned dataset. Evaluation of Linear Regression and Ridge Regression was done using regression metrics while Logistic Regression was evaluated using classification metrics (ROC-AUC). Further insight was provided through threshold analysis and bootstrap confidence intervals.