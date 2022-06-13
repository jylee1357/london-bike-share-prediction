# London Bike Share Prediction
### 🙋‍♂️ Goals
- Using Kaggle's 'London Bike Share Dataset', I tried to predict the demands for bikes in London.
- Compared DNN, Random Forest Regressor, XGBRegressor and LGBMRegressor
- Made prediction using RNN,LSTM,GRU (based on Time Series)
### 𝌞 Data Preprocessing
* Kaggle Datasets  
   <img width="689" alt="Screen Shot 2022-06-13 at 9 43 15 PM" src="https://user-images.githubusercontent.com/98932859/173356366-869ab439-752f-4908-9e9a-2c5ed5637a69.png">
   
  |Variable|Explanation|
  |------|---|
  |timestamp|Time of Rental|
  |cnt|Number of users|
  |t1|Temperature|
  |t2|Windchill Temperature|
  |hum|Humidity|
  |wind_speed|Wind Speed|
  |weather_code|Weather Code by Category|
  |is_holiday|Whether the day is holiday|
  |is_weekend|Whether the day is weekend|
  |season|Season|
  
* Preprocessing
  - Divided 'timestamp' by year, month, day of week, and hour
     <img width="671" alt="Screen Shot 2022-06-13 at 9 56 47 PM" src="https://user-images.githubusercontent.com/98932859/173358820-f52f57a5-07cc-4604-abb3-9ae2d9690611.png">
    
  - Removed outliers     
     <img width="669" alt="Screen Shot 2022-06-13 at 9 59 00 PM" src="https://user-images.githubusercontent.com/98932859/173359110-4b9d1177-73af-4016-9f6e-5a9ae52a8942.png">

    
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
