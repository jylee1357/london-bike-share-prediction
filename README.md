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

  - Changed 'weather_code', 'season', 'year', 'month', 'hour' into dummy variables    
     <img width="672" alt="Screen Shot 2022-06-13 at 10 01 31 PM" src="https://user-images.githubusercontent.com/98932859/173359580-a88feb14-238c-437b-8d87-7b30fd9ca64f.png">  
    

### ⌨️ Models
* Model Comparison 
  - Deep learning model's RMSE
    <img width="1040" alt="Screen Shot 2022-06-13 at 10 11 43 PM" src="https://user-images.githubusercontent.com/98932859/173361479-b682afb8-11ab-4e81-9b52-cdabe619b8ac.png">
    <img width="1028" alt="Screen Shot 2022-06-13 at 10 13 31 PM" src="https://user-images.githubusercontent.com/98932859/173361722-89449368-f598-4d7f-abc2-5d705319e0ac.png">  
    
   - Time series model's RMSE
    <img width="997" alt="Screen Shot 2022-06-13 at 10 17 13 PM" src="https://user-images.githubusercontent.com/98932859/173362374-c2c3510f-da8d-4365-8b4d-ebf1375be862.png">
    
### 📍 Takeaway
* The determinant features that enhanced model's performance were 'DAYS_BIRTH', 'AMT_CREDIT', 'CREDIT_SCORE'.
* After cross-validation, the model's final score improved by 0.03.
