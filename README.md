# Driver_Prediction
Predict which driver should be assigned a cab ride order. Details about the rides and driver's response for 10 days is provided and predictions have to be done for the 11th day.
Trained Logistic regeression to predict which driver should be assigned a cab ride order. Details about the rides and driver's response for 10 days is provided and predictions have to be done for the 11th day.

Computed temporal(day_of_week, is_busy_hour), geographical(haversine distance between pickup and drop location), driver(driver_location_cluster and customer_location_cluster trained by K Means, driver_response_time). #and other features along with rolling mean and median across days for feature engineering.

Metrics : In this problem, we want that a ride should be assigned to the driver with the highest possibility of acceptance. So, precision over recall is important. Because precision is (TP/(TP+FP)) which means of all the drivers that we assigned a score of 1, how many were actually correct.

80\% of the times ride was assigned to the correct driver.

Note : We assign a class 1 only to one driver per order ID in the model predictions while in the actual available data, more than one drivers can have class label one per order ID. So accuracy wil go down because of this reason and we might get a wrong picture.

Need to work a little more on metrics because :

![image](https://user-images.githubusercontent.com/32570848/155849447-a76ebd76-5aaa-4892-bbdd-5c5760053e94.png)

   
In the above example, we could not assign the rider a correct driver and labelled both the correct ones as wrong. This case can be perfectly captured if I calculate precision as well as recall where a perfect recall for our case would be that I am able to capture atleast one correct driver out of all per order ID.   
