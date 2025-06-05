**📁 Dataset**
Source: Kaggle - Credit Card Fraud Detection

Features:
28 anonymized PCA-transformed features: V1 to V28
Time and Amount
Target variable: Class (0 = Non-Fraud, 1 = Fraud)

**📊 Exploratory Data Analysis**

Verified absence of missing values.
Performed distribution analysis on:
Time and Amount per class
Selected PCA components (V4, V10, V12, V14, V17)
Noted severe class imbalance: ~0.17% Fraud cases

**🧹 Preprocessing**
Standardized Time and Amount using StandardScaler
Left PCA features as-is
Applied StratifiedKFold (5 splits) for robust cross-validation

**🧠 Models Used**
All models were tuned using GridSearchCV with F1-score as the scoring metric:

**Model	Notes**
Logistic Regression	Weighted (class_weight='balanced')
Decision Tree	Depth and leaf size tuned
Random Forest	Tuned for depth, estimators, and leaves
XGBoost	Adjusted scale_pos_weight for imbalance

**🔍 Evaluation Metrics**
Each model was evaluated on:

Accuracy (less meaningful due to class imbalance)
Precision (how many predicted frauds were correct)
Recall (how many actual frauds were detected)
F1-Score (harmonic mean of precision and recall)
ROC AUC (area under ROC curve)
Confusion Matrix

**📈 Feature Importance**
Tree-based models (Decision Tree, Random Forest, XGBoost) visualized top 10 most important features.
Logistic Regression coefficients were ranked to show strongest predictors.

**🏆 Best Performing Model**
Based on F1-Score for Fraud Class:
Best Model:XGBoost

**💡 Key Takeaways****
Class imbalance significantly affects model performance. F1-score and recall are more informative than accuracy.
Scaling only necessary features avoids distorting PCA components.
XGBoost generally performs well with imbalance when scale_pos_weight is correctly set.
Feature importance can help identify signals of fraudulent behavior.
