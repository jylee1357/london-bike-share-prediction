# London Bike Share Prediction
### 🙋‍♂️ Goals
- Using Kaggle's 'London Bike Share Dataset', I tried to predict the demands for bikes in London.
- Compared DNN, Random Forest Regressor, XGBRegressor and LGBMRegressor
- Made prediction using RNN,LSTM,GRU (based on Time Series)
### 𝌞 Data Preprocessing
* Datasets
  - application_train.csv
  - application_test.csv
  - bureau.csv
  - bureau_balance.csv
  - credit_card_balance.csv
  - installments_payments.csv
  - POS_CASH_balance.csv
  - previous_application.csv
   
* Preprocessing
  - application_train.csv
    + Use Pandas factorize() on object columns
    + In "DAYS_EMPLOYED" column, there are outliers (EMPLOYED DAYS > 1,000); therefore, I decided to remove it.
  - Previous_application_train.csv
    + Merged with application_train.csv
    + Used aggregation to apply all the preprocessing functions on each 'SK_ID_CURR' and saved the result as a new dataframe
 * Feature Engineering
   - Created new factors using amt_credit
      +  <img width="1000" alt="Screen Shot 2022-06-11 at 8 53 20 AM" src="https://user-images.githubusercontent.com/98932859/173163734-fa502127-3a23-479f-8fa3-ca98522194dd.png">
    - Using 'amt_income_total', features regarding client's loan were manipulated. 
      +  <img width="1000" alt="Screen Shot 2022-06-11 at 8 53 20 AM" src="https://user-images.githubusercontent.com/98932859/173164029-6706e1d9-627d-4f26-bec7-8c8d995ffe71.png">
   - Using 'DAYS_BIRTH' and 'DAYS_EMPLOYED', features regarding income were manipulated.
      +  <img width="1001" alt="Screen Shot 2022-06-11 at 9 01 57 AM" src="https://user-images.githubusercontent.com/98932859/173164154-a9b36ed4-ff95-4baf-9dbc-71d52969d634.png">

### ⌨️ Models
* LGBM Classifier
  - app_baseline (score: 0.74448)
    + <img width="993" alt="Screen Shot 2022-06-11 at 9 11 04 AM" src="https://user-images.githubusercontent.com/98932859/173164592-e0d9bdd8-08d7-4915-bb97-701b25025bea.png">
  - prev_baseline (score: 0.77574)
    + <img width="1000" alt="Screen Shot 2022-06-11 at 9 12 44 AM" src="https://user-images.githubusercontent.com/98932859/173164665-f87cf00a-f915-4299-b328-b811e8ec0b22.png">
* Hyperparameter Tuning
  - Used Bayesian Optimization to tune hyperparameters of models that were created using application & previous train datasets.
  - Set values for search
  - For each iteration, hyperparameters are updated and using the parameters, classifiers were trained. The roc_auc_score was returned as well.
  - Using the best hyperparameters, classifier was tested again. 
  - Tuning the hyperparameters by performing cross-validation (final score: 0.79787)
    + <img width="966" alt="Screen Shot 2022-06-11 at 9 41 05 AM" src="https://user-images.githubusercontent.com/98932859/173165850-0fb75716-4fe0-400b-ace5-0f797d2b050d.png">
    + <img width="956" alt="Screen Shot 2022-06-11 at 9 41 55 AM" src="https://user-images.githubusercontent.com/98932859/173165885-3659cfef-c3b7-4b3b-8a3d-002ee1d08640.png">
    
### 📍 Takeaway
* The determinant features that enhanced model's performance were 'DAYS_BIRTH', 'AMT_CREDIT', 'CREDIT_SCORE'.
* After cross-validation, the model's final score improved by 0.03.
