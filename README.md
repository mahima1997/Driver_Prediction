# Driver_Prediction

DATA:
**bookings.log (7 lac rows)**

| timestamp | order_id | booking_status | customer_id | driver_id | trip_distance | pickup_lat | pickup_long | 
booking_status : CREATED/DRIVER_FOUND/PICKED_UP/COMPLETED

**participant.log (6 lac rows)**

| timestamp | order_id | participant_status | experiment_id | driver_id | trip_distance | driver_lat | driver_long | driver_gps_accuracy |
participant_status: CREATED/ACCEPTED/IGNORED/REJECTED

**test_data (1 lac rows)**

| timestamp | order_id | customer_id | driver_id | trip_distance | driver_lat | driver_long | driver_gps_accuracy | pickup_lat | pickup_long | 


Predict which driver should be assigned a cab ride order. Details about the rides and driver's response for 10 days is provided and predictions have to be done for the 11th day. Test data has 10 drivers for every order and the question is to predict if that driver should be assigned a ride.

Following is the distribution of Drivers per order_id to know that how many drivers data is available per order id    	

![image](https://user-images.githubusercontent.com/32570848/163670754-6abb61be-5c88-4f5b-86ec-19f4930e4972.png)


Below is the count for presence of classes in the dataset. 1 means ride ACCEPTED while 0 means IGNORED/REJECTED.
The below observation indicated imbalanced dataset.

![image](https://user-images.githubusercontent.com/32570848/163670770-f19f6035-39f3-4a93-97ea-fde7389c190e.png)

SMOTE was performed on training data to create synthetic data by upsampling.

Trained Random Forest to predict which driver should be assigned a cab ride order. Details about the rides and driver's response for 10 days is provided and predictions have to be done for the 11th day.

Computed temporal(day_of_week, is_busy_hour), geographical(haversine distance between pickup and drop location), driver(driver_location_cluster and customer_location_cluster trained by K Means, driver_response_time).

Following result was obtained when Random Forest was trained.

              precision    recall  f1-score   support

           0       0.91      0.93      0.92      3846
           1       0.99      0.99      0.99     36051

    accuracy                           0.98     39897
   macro avg       0.95      0.96      0.95     39897
weighted avg       0.98      0.98      0.98     39897

******************************************************************************************************************************************************************
When dealing with probability output, below points are considered:

Metrics : In this problem, we want that a ride should be assigned to the driver with the highest possibility of acceptance. So, precision over recall is important. Because precision is (TP/(TP+FP)) which means of all the drivers that we assigned a score of 1, how many were actually correct.

80\% of the times ride was assigned to the correct driver.

Note : We assign a class 1 only to one driver per order ID in the model predictions while in the actual available data, more than one drivers can have class label one per order ID. So accuracy wil go down because of this reason and we might get a wrong picture.

Need to work a little more on metrics because :

![image](https://user-images.githubusercontent.com/32570848/155849447-a76ebd76-5aaa-4892-bbdd-5c5760053e94.png)

   
In the above example, we could not assign the rider a correct driver and labelled both the correct ones as wrong. This case can be perfectly captured if I calculate precision as well as recall where a perfect recall for our case would be that I am able to capture atleast one correct driver out of all per order ID.   
