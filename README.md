# Churn-Prediction-by-Kishor-Desai
**Churn Rate Prediction**
This code implements a customer churn prediction pipeline. It generates a synthetic dataset, preprocesses the data, trains a RandomForestClassifier using hyperparameter tuning, evaluates the model, and visualizes feature importance.
________________________________________
**Problem Statement**
Goal: Predict customer churn (whether a customer will stop using a service) using demographic, behavioral, and account-related features.
•	Businesses lose significant revenue due to churn, and predicting churn allows proactive retention strategies like personalized discounts or improved customer support.
•	This solution helps identify the most influential factors contributing to churn.
________________________________________
Data Description
The synthetic dataset consists of 10,000 customers and the following features:
1.	**Demographic Information:**
a.	  **Age**: Customer's age.
b.  	**Gender**: Male or Female.
c.  	**City**: Urban, Suburban, or Rural.
d.  	**IncomeGroup**: Low, Middle, or High income.
2.	**Behavioral Information:**
a.  	**ServiceUsageHours**: Weekly usage of the service in hours.
b.  	**SupportTicketsRaised**: Number of support tickets raised by the customer.
c.  	**Complaints**: Number of complaints raised.
d.  	**LatePayments**: Count of late payments.
e.  	**DiscountReceived**: Amount of discount offered to the customer.
3.	**Account Information**:
a.  	**Tenure**: Number of months the customer has been with the service.
b.  	**MonthlyCharges**: Monthly billing amount.
c.  	**TotalCharges**: Total billing amount (calculated as MonthlyCharges * Tenure).
d.  	**PaymentMethod**: Payment type (e.g., Credit Card, PayPal).
e.  	**ContractType**: Contract type (Month-to-month, One year, Two years).
f.  	**InternetService**: Type of internet service (Fiber optic, DSL, None).
4.	**Target Variable**:
a.  	**Churn**: Binary variable (1 = Customer churned, 0 = Customer retained).
________________________________________
**Feature Engineering Steps**
1.	**Derived Features:**
a.  	**CLV** (Customer Lifetime Value): Computed as MonthlyCharges * Tenure. This represents the total revenue a customer brings to the business during their tenure.
2.	**Categorical and Numerical Features:**
a.  	Categorical features (Gender, PaymentMethod, etc.) are encoded using OneHotEncoder.
b.  	Numerical features (Age, MonthlyCharges, etc.) are standardized using StandardScaler.
________________________________________
**Model Pipeline**
1.	**Preprocessing**:
a.  	A ColumnTransformer is used to: 
o       Scale numerical features.
o	      One-hot encode categorical features.
2.	**Model**:
a.  	A RandomForestClassifier is used to predict churn.
b.  	Hyperparameter tuning is performed with GridSearchCV, optimizing for ROC AUC score.
3.	**Pipeline**:
a.  	Combines preprocessing and model steps into a single pipeline for seamless training and evaluation.
4.	**Hyperparameters Tuned**:
a.  	n_estimators: Number of trees in the forest.
b.  	max_depth: Maximum depth of each tree.
c.  	min_samples_split: Minimum number of samples required to split a node.
5.	**Model Evaluation**:
a.  	classification_report provides metrics such as precision, recall, F1-score, and support for churned and non-churned classes.
6.	**Feature Importance**:
a.  	Extracted from the RandomForestClassifier to determine which features contribute most to the predictions.
________________________________________
**Key Insights from KPIs**
1.	**Model Performance**:
a.  	The classification report indicates how well the model predicts churn and retention. Look at metrics like precision, recall, and F1-score for the churned class (1).
2.	**Feature Importance**:
a.  	The bar chart of feature importances identifies the key factors influencing churn: 
o	     Tenure: High tenure decreases churn likelihood.
o	     ContractType: Customers with "Month-to-month" contracts are more likely to churn.
o	     DiscountReceived: Discounts impact churn reduction.
o	     InternetService: Fiber optic customers show different churn patterns than DSL or None.
3.	**Churn Prediction Use Case**:
a.  	Businesses can use the model predictions and feature insights to: 
o	     Target customers likely to churn with retention offers.
o	     Improve customer experience by addressing major complaints or service issues.
________________________________________
**Next Steps**
1.	**Deployment**:
o	   The trained pipeline can be deployed to predict churn for new customers in real time.
2.	**Business Strategy**:
o	   Use the predictions to create personalized retention strategies.
o	   Focus on customers with high churn probability and high Customer Lifetime Value (CLV).
