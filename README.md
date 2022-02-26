# Driver_Prediction
Predict which driver should be assigned a cab ride order. Details about the rides and driver's response for 10 days is provided and predictions have to be done for the 11th day.
Trained Logistic regeression to predict which driver should be assigned a cab ride order. Details about the rides and driver's response for 10 days is provided and predictions have to be done for the 11th day.
Computed temporal, geographical, driver and other features along with rolling mean and median across days for feature engineering.

Metrics : In this problem, we want that a ride should be assigned to the driver with the highest possibility of acceptance. So, precision over recall is important. Because precision is (TP/(TP+FP)) which means of all the drivers that we assigned a score of 1, how many were actually correct.

80\% of the times ride was assigned to the correct driver.
