#  Identify  Client who will Subscribe to Term Deposit 
Our dataset comes from the UCI Machine Learning repository link. 
The data is from a Portugese banking institution and is a collection of the results of 17 marketing campaigns. 
 The classification goal is to predict if the client will subscribe a term deposit (variable y). We perform K Nearest Neighbors,Logical Regression, Support Vector Classifier, Decision Tree Classifier and identify which performed best with this data and also identify the columns that matter the most .


Dataset Used is found [here](/data/bank-additional.csv)  
All the prompts given to achieve the below analysis can be found [here](/bank_predictdeposit.ipynb).  

Here's a breakdown of the key steps and insights:
NOTE: All the analysis of models performed on small dataset to minimize the time for GridSearch 

**1. Understanding the Features:**

* **Data Inspection:** The code starts by removing duplicate records from the data
* **Visualizations:**  Scatter plots are generated to visualize the relationship between various features (categorical and numerical features) and the target variable ('price'). These visualizations help understand the correlation and potential non-linear relationships.  
* **Correlation Analysis:** The correlation between numerical features and the target variable yis calculated.  The code determines the most correlated feature to price.
* **Data Distribution:**  Examining the value counts for numerical columns shows distribution, which informs cleaning and transformation strategies.
* ** DataType Conversion: **Converting data to appropriate datatypes

**2.Understanding the Task :**
Identify the key customer demographics, behaviors, and economic factors that influence client's decision to subscribe to a term deposit. Use this information to optimize marketing campaigns, target specific customer segments, and increase term deposit subscription rates

**3. Engineering Features:**
* **Feature Scaling & Encoding:**  Numerical features are scaled using `StandardScaler`.  Categorical features are encoded using `JamesSteinEncoder`.  Polynomial features are added.
Mean Imputer was performed on Numerical Features
Most frequent Imputer was performed on Categorical features,

**4.Train-Test Split:** Data is split into 80% training and 20% testing sets.

**5. BaseLineModel:**  Dummy Classifier with strategy Most frequent was used to train the training set . Also used Confusion Matrix to display TruePositive, True Negative, False Positive and False Negative

**6: Logistic Regression:** A logistic regression model is trained and evaluated using Precision,REcall,F1Score and ConfusionMAtrix

**7: Score Model:** Logistic Regression gave 90% accuracy score.

**8:Model Comparisons:**  Run KNN, Decision Tree, Logistic Regression and SVM with default parameters and observe the accuracy score on test data
On test data,Logistic Regression and KNN were more accurate than decision tree and SVM

**9:Improving Model:** 
* **Hyperparameter Tuning (GridSearch):** Hyperparameter tuning is performed on all the models.

 best KNN Parameters are {'metric': 'minkowski', 'n_neighbors': 25, 'weights': 'uniform'}
Accuracy with best hyperparameters: 0.8968446601941747

Best hyperparameters for Decision Tree: {'criterion': 'entropy', 'max_depth': 30, 'max_features': None, 'max_leaf_nodes': 20, 'min_samples_leaf': 1, 'min_samples_split': 2, 'splitter': 'random'}
Accuracy of best Decision Tree Model: 0.9016990291262136

Best hyperparameters for SVM: {'C': 0.1, 'degree': 2, 'kernel': 'linear'}
Accuracy of best SVM Model: 0.9053398058252428

So, considering the precision_score, recall_score and f1_score for SVM, LogisticRegression, DecisionTree and KNN, SVM: {'C': 0.1, 'degree': 2, 'kernel': 'linear'}
Accuracy of best SVM Model: 0.9053398058252428
    
Observing the feature importance and their coefficients,poly__duration,num__euribor_3_month_rate ,consumer_confidence_index have high importance . So clients with higher duration and euribor_3_month_rate and higher consumer_confidence_index is most likely to subscribe to term deposit
