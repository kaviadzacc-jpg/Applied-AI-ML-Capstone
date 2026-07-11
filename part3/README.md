Part 3: Advanced Modeling – Ensembles, Hyperparameter Tuning and Machine Learning Pipeline

The objective of this project is to compare multiple ensemble learning algorithms, perform hyperparameter tuning, build a reusable machine learning pipeline, evaluate model performance using cross-validation, and save the best-performing model for future use.

Dataset
Dataset: Medical Insurance Cost Dataset
Rows: 1338
Columns: 7
Classification Target: charges > median(charges)

Data Preparation
The cleaned dataset from Part 2 was used.Categorical variables were converted using One-Hot Encoding.The dataset was split into training and testing sets.StandardScaler was applied after the train-test split.

Decision Tree
Two Decision Tree models were trained.

Controlled Decision Tree
The controlled model reduced overfitting and improved generalization.

Random Forest
The following metrics were reported.
1) Training Accuracy
2) Testing Accuracy
3) ROC-AUC
Top five feature importance values were extracted.Random Forest computes feature importance using the average reduction in Gini impurity across all trees.

Bagging
Random Forest uses bootstrap sampling.Every tree is trained on a different random sample of the training data.At every split, only a random subset of features is considered.Combining predictions from many trees reduces variance and improves generalization.

Gradient Boosting
Gradient Boosting sequentially trains trees where every new tree attempts to correct the mistakes of previous trees.
1) Training Accuracy
2) Testing Accuracy
3) ROC-AUC
were reported.

Feature Ablation
The five least important features identified by the Random Forest were removed.A second Random Forest was trained.The ROC-AUC of the reduced model was compared with the original model.If the AUC remained similar, the removed features were considered largely uninformative.

Cross Validation
5-fold Stratified Cross Validation was performed.
Models evaluated
1) Logistic Regression
2) Controlled Decision Tree
3) Random Forest
4) Gradient Boosting
Mean ROC-AUC and Standard Deviation were reported.Cross Validation provides a more reliable estimate of model performance because every observation is used for both training and validation.

Parameter Grid
1) n_estimators
2) max_depth
3) min_samples_leaf

Model Serialization
The best pipeline was saved using
joblib.dump()

The model was successfully reloaded using
joblib.load()

Final Model Comparison
A comparison table was created for
1) Logistic Regression
2) Decision Tree
3) Random Forest
4) Gradient Boosting
using,
1) Mean Cross Validation AUC
2) Standard Deviation
3) Test ROC-AUC
The model with the best balance of accuracy and generalization was recommended for deployment.

Files Included
1) cleaned_data.csv
2) best_model.pkl
3) part3.ipynb
4) README.md
5) requirements.txt

Multiple ensemble models were trained and compared.Random Forest and Gradient Boosting produced stronger predictive performance than a single Decision Tree.Hyperparameter tuning improved model selection.The final pipeline was successfully serialized and can be reloaded for future predictions.