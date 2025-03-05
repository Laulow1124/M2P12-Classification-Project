# M2P12 Classification Project
--------

**The objective of the M2P12 Classification Project is to to create a model to predict whether or not a customer will churn.**

**The material applied from Module 2 will be the following:**
1. Feature Engineering and Data Preprocessing
2. Logistic Regression
3. K Nearest Neighbours (KNN)
4. Decision Trees and Random Forests

**M2P12 Classification Project has the following conditions:**
1. Project must include EDA section.
2. Project must include visualization.
3. Data must be cleaned and prepared.
4. Use Feature Engineering, if applicable.
5. Must compare at minimum 3 classification models.
6. Provide validation scheme (simple or cross-validation).
7. Explain which feature(s) are chosen for final model.
8. Use final model to make new predictions based on my provided input.

**The outline for the project will be the following:**

**The project will be split into five parts:**
1. Part 1 will involve EDA, Visualization, Data Cleaning, Encoding, Data Preparation (ex: Split to X and y).  <br>
2. Part 2 will be working with Model #1: Logistic Regression. <br>
3. Part 3 will be working with Model #2: K Nearest Neighbours (KNN). <br>
4. Part 4 will be working with Model #3: Random Forest (Classifier). <br>
5. Part 5 will be determining which of the three models has the best performance and having the best performing model be our final model. <br>
   The final model will be used to make a prediction and includes some final comments/conclusion. <br>

**Conditions checklist:** <br>

**1. Project must include EDA section.**
   - Found in Part 1 in M2P12 project notebook. <br>
   
  <u>Observations from EDA:</u>
- 'Churn Reason' has 5174 missing values.
- 'Total Charges' is an object. 'Total Charges' will need to be converted to be numeric (int, float), but without encoding. 
- The other features which are objects will either be removed or will be converted to be numeric. (int, float)

**2. Project must include visualization.**
   - Found in Part 1 in M2P12 project notebook.
   - Includes bar plots and scatterplots in Part 1. <br>
   
  <u>Observations from Visualization:</u> 
- More occurrences of Churn at higher Monthly Charges.
- More occurrences of Churn with the 'Month-to-month' Contract Type.
- More occurrences of Churn (compared to No Churn) seen at lower Tenure (Months) and higher Monthly Charges.
    
**3. Data must be cleaned and prepared.**
   - Found in Part 1 in M2P12 project notebook.  
   - Data preparation includes splitting data into X and y. (Later put into X_train, X_test, y_train and y_test).
     
  <u>Dropping Unnecessary Features:</u> <br>
- Dropping features with unique values for every row/customer ('CustomerID', 'Count', etc.): they don't provide any meaningful information about customer behavior or characteristics. <br>
- Dropping features related to location ('State', 'Lat Long', etc.): all customers are within the same country and state, there would have little to no variance, which would contribute little to predicting churn. <br> 
- Dropping Churn Value: This is already in Churn Label, which will be encoded. <br>
- Dropping Churn Score: This feature is likely derived or unnecessary, and is too closely related to Churn Label as target variable. <br>
- Dropping Churn Reason: This is a text-based column, not usable for training models as there could be too many catergories and sparse data. <br>

**4. Use Feature Engineering, if applicable.**
- Found in Part 1 in M2P12 project notebook.
- For Logistic Regression and the K Nearest Neighbours (KNN), scaling (StandardScaler) was used.
  
  <u>Reasoning for encoding data for Classification models:</u> <br>
- Classification models require numerical data (as input) to understand patterns to provide a predictive output. <br>

  <u>Encoders used, converting features to numerical data:</u> <br>
- 'Total Charges' feature has dtype "object" but they are strings of numerical values. This feature was converted to have numerical values.
- Label Encoding on features with binary choices/values.(ex: Male or Female, Yes or No to 0 and 1). Used for its simplicity and efficiency. 
- One Hot Encoding on features with multiple choices/values (greater than 2 choices). Label Encoding may lead the algorithm to believing that multiple values could be ordinal values (there is ranking). One Hot Encoding would prevent misinterpretation of ordinal relationships.

**5. Must compare at minimum 3 classification models.**
   - The three classification models to be compared: Logistic Regression, K Nearest Neighbours (KNN) and Random Forest (Classifier).
   - Part 2 will be working with Model #1: Logistic Regression.
   - Part 3 will be working with Model #2: K Nearest Neighbours (KNN).
   - Part 4 will be working with Model #3: Random Forest (Classifier).
   - Part 5 will compare performance of all three models.
     
**6. Provide validation scheme (simple or cross-validation).**
   - Found in Part 2, Part 3 and Part 4 in M2P12 project notebook.
   - Cross-validation (with GridsearchCV) was used on all three models to evaluate and acquire the best parameters for each model.
   - Cross-validation was used to evaluate the holdout data, and has (somewhat) similar results/metrics with the test data.

**7. Explain which features are chosen for final model.**
   - Found in Part 1 and Part 5 in M2P12 project notebook.
   - Final model was Logistic Regression.
   - Features chosen: Gender, Senior Citizen, Partner, Dependents, Tenure Months, Phone Service, Multiple Lines, Online Security, Online Backup, Device Protection, Tech Support, Streaming TV, Streaming Movies, Paperless Billing, Monthly Charges, Total Charges, CLTV, Internet Service_Fiber optic, Internet Service_No, Contract_One year, Contract_Two year, Payment Method_Credit card (automatic), Payment Method_Electronic check, Payment Method_Mailed check
   - Features which deal with demographics, performance, service, plans, offerings/benefits, payments and time duration were chosen as they could influence churn.
   - The Logistic Regression model had scaling, as it makes it more efficient.    

**8. Use final model to make new predictions based on my provided input.**
   - Found in Part 5 in M2P12 project notebook.
   - As per prediction experimentation, with "new_data (data frame)" as input, the Logistic Regression Model was able to provide a prediction of No Churn (0) or Churn (1).

## Conclusion 
In conclusion, three models were tested: Logistic Regression, K Nearest Neighbours (KNN) and Random Forest (Classifier). <br>
**Of the three models, the Logistic Regression model had the best performance as it has the highest Churn F1-Score, as well as a good balance between Churn Precision, Churn Recall and Accuracy.** <br>

- For chosen features (applied to final model, Logistic Regression): features which deal with demographics, performance, service, plans, offerings/benefits, payments and time duration were chosen as they could influence churn. <br>
- Cross-validation (with GridSearchCV) was used for all three models. The reason is so we could evaluate the best parameters in a similar method before choosing final model. Cross-validation was used to evaluate the holdout data, and has (somewhat) similar results/metrics with the test data.<br>
- All three classification models required the data to be converted into numerical format hence the use of encoding. For features with binary values, LabelEncoder was used for encoding. For features with three or more values, OneHotEncoder was used. <br>   
- With what was stated above, the final model (Logistic Regression) had the encoding feature LabelEncoder for features with binary values and OneHotEncoder for features with three or more values. These encoders were applied as part of feature engineering for the final model (Logistic Regression). <br>  
- Continuing with feature engineering, scaling was applied on the data for the final model (Logistic Regression), as it makes it more efficient. <br>
- As per prediction experimentation, with "new_data (data frame)" as input, the Logistic Regression Model was able to provide a prediction of No Churn (0) or Churn (1). <br>
