# Prepaid Mobile Customer Churn Prediction
## Business Case
* In all industries, customer churn has been a real problem, and gaining new customers has been far more expensive than keeping existing ones. 
* While there are many reasons for customer churn, dissatisfaction with services, subscriptions that are costly, and better alternatives are some of the most common.
* Thus, in our analysis of pre-paid phone customers, the reasons for churning are addressed and factors affecting the churn are examined for their impact.
## Data Summary
* The Customer Churn dataset is a record of the pre-paid phone customer usage over a span of three months from June to August 2013 and a list of customers that did/didn’t drop the service in September of that year.
* 'Churn' is the target variable that indicates whether the customer retained the service or not in September 2013. 
* The data set had 193 columns and 1,82,343 rows. 
* After preprocessing, the dataset has 71 columns and 66,469 rows.
## Multicollinearity Check
![image](https://user-images.githubusercontent.com/48169929/226159416-1df2fa3f-19e6-40fc-807a-19aad7a6a6c8.png)
## KeyObservations
### Plot between user_intake, gprs usage, gprs spendings for all months
* For months 6 and 7, for the old customers and those who are staying back, the spending is increasing with their usage of data for most of the customers.  
* While for month 8, most of their spending was not increasing and they were constant. 
* For old customers and for those who left, there is an increase in spending on data with a small increase in the usage of the data.
  ![image](https://user-images.githubusercontent.com/48169929/226159603-15516e29-7b53-4de6-a720-1865e019e29f.png)
### Plot between the amount spent on outgoing calls and the duration of all outgoing calls.
* In month 6, we can see that old customers' spending is increasing with their call durations increasing. However, some customers' spending rapidly increases with a small increase in the call duration.
* In the case of new customers, the spending increases for all of them as the call duration increases.
![image](https://user-images.githubusercontent.com/48169929/226159719-26b4c7e9-d3b2-4ecc-9e03-744ea4d72b22.png)
## Model Comparison
### Model Accuracies without sampling:
1. LogisticRegression():   0.8895157498824636
2. DecisionTreeClassifier(random_state=1): 0.8456229431123647
3. RandomForestClassifier(random_state=1): 0.8891020216267043
4. GradientBoostingClassifier(random_state=1): 0.8932769158439117
5. XGBClassifier(random_state=1): 0.8931264692054537
6. SVC: 0.8912646920545368

### Model Accuracies with oversampling:
1. LogisticRegression() : 0.8487954424738626
2. DecisionTreeClassifier(random_state=1) : 0.9328759509073985
3. RandomForestClassifier(random_state=1) : 0.9583818948320083
4. GradientBoostingClassifier(random_state=1) : 0.8613878923099471
5. XGBClassifier(random_state=1) : 0.8615662669597028

### Model Accuracies with undersampling:
1. LogisticRegression() : 0.846889531199907
2. DecisionTreeClassifier(random_state=1) : 0.7976360519918513
3. RandomForestClassifier(random_state=1) : 0.851877861053822
4. GradientBoostingClassifier(random_state=1) : 0.8541698949106248
5. XGBClassifier(random_state=1) : 0.8538551266095993

* We can observe that **GradientBoosting Classifier** is the best performing model with as accuracy of **0.8932**.
* We can see that RandomForest Classifier gave the best accuracy of 95.93% with over sampling. But, after doing the hyper parameter tuning, the train data accuracy was better and the test data accuracy was not good and the model was overfitting. We have also tried cv by doing PCA( 8 components) before and the accuracies of the cv were 1.0 for the models. It could capture only 72% of the data. It is over fitting to the data. So, we are going to proceed the modeling part without sampling the data and PCA.






## Recommendations
1. New users are more likely to leave the service when compared to old customers.
![image](https://user-images.githubusercontent.com/48169929/226159774-e8c3e756-688b-46bc-95bd-5ee34b920d57.png)
2. When we are predicting customer retention for a month, we could see that if the SMS outgoing inactivity days is more than 24, then there is a high chance that the customer might leave the service.
![image](https://user-images.githubusercontent.com/48169929/226159790-09860a6e-eb09-4854-ad17-a7e0226d8e75.png)

**Based on these customer Behaviors we recommend**
To retain the existing customers,  the service providers should start pre-paid plans with unlimited calls and SMS, including a data plan up to a limit of certain KBs of usage, beyond which they will be charged extra. This will also bring in new customers and reduce the inactivity of the customers.





