# AIRBNB-Price-Prediction
The project aims at using ML and Neural Nets to predict the price of a new booking based on various features.
This dataset(modified from the original dataset on Kaggle) was used as a 'Final Project' for Data Science-I class at 'The University of Illinois Chicago'. This data set is available through Kaggle competetion.
Link: https://www.kaggle.com/c/airbnb-recruiting-new-user-bookings
We were asked to use material presented to us in the class: Linear, Lasso, Ridge, Logistic, KNN and ANN.


IMPUTATIONS:

1.	There are several types of imputations performed. For columns with text and special characters were replaced with appropriate strings such as 'Not Available' or 'No Dates Available'. 

2.	The other numeric columns such as bathrooms or beds are replaced with the lowest number of available numeric constant. In most, cases they are replaced with ‘0’.

3.	The ‘ZipCode’ column has many variations in it. They were tricky to handle and had many different types of constants and literals. I tried replacing the entire column using .re but was unsuccessful. However, I used the ‘Latitudes and ‘Longitudes to produce the zip codes column which entirely replaces the original one with some variations in it.

GRAPHS:

1.	Basic plots of City-counts and variance, bar plots indicating mean of ‘Apartment Price’ per city. I also checked the average price of apartments if,  1. host_has_profile_pic 2.host_has_identity_verified. It is not surprising to see the results though. 

2.	Correlation heat map of all variables in the data frame. This is indicative of which attributes are closely related. For eg: Accommodates and (bedroom, beds, apartment_type are closely related)

3.	Grid Plots of ['bedrooms', 'bathrooms', 'accommodates', 'beds'] w.r.t ‘City’ gives us a good indication of distribution of all attributes with ‘City.

FEATURE SELECTION:

1.	The feature selection used in the whole project is ‘Principal Component Analysis (PCA). This is primarily because; using PCA reduces the linear dimensionality using SVD of data to a lower dimension. I tried implementing different models using pca(0.99 or 0.8). However, it gives me the best result when the function decides to reduce by itself.

2.	I also tried implementing ‘Stepwise Forward Selection’. However, since we have many attributes, the code was running for a long time with limited results and hence, I moved forward with PCA.

THIRD MODEL:

1.	The 3rd model that I implement is ‘LASSO Regression with L1 as 0.0001.

2.	It is better than linear and Ridge with accuracy improved by 2%. 

3.	I started with alpha value as 1 which was completely linear and hence it had the lowest accuracy. With some trial and error, 0.0001 which would try to fit the model with lower deviations and hence more MSE. 



CLASSIFICATION


IMPUTATIONS:
1.	For the classification part, the only difference is instead of ‘log_price’ we have to drop property type and also they have not been ONE HOT ENCODED. Everything else remains the same.


GRAPHS:
1.	The first plot indicated the # of count of every type of ‘apartment_type’. This gives us a visual of distribution of all type properties.
2.	I was trying to find co-relation between ['city', 'log_price', 'cancellation_policy'] vs ‘property_type. This also shows that ‘apartment’ is most prominent.
3.	The graph of [‘city’, ‘log_price’, ‘bedrooms’] vs property_type gives us a good visual of how the Price varies with property_type in every city.


THIRD MODEL ‘SVM’:
1.	SVM’s are usually used for data with many dimensions. Since we have 74111 X 29 times data. Even by applying SVM to train data, it may not be able to extract the subset of training points. Even if we try to run it for an extended period of time, it may over-fit the train data. Also, we could use regularization to avoid over-fitting, but since it is time and memory intensive, it may not be the best method to proceed with.


BEST MODEL:
1.	The best model that I implemented is by using just the ‘description’ column without applying PCA or any feature reduction technique. It gives a robust accuracy of 80.49%. 

2.	The best model that I implemented is KNN (from KNN, Logistic regression and SVM) which gives a Train accuracy of 66.12% using 500 neighbors. I implemented 5, 10, 50, 100, 500, 1000 and the accuracy saturated at 500 starting from 32% to 68% for 1000 neighbors.

3.	There seems to be something off with Logistic regression as, I tried implementing it with 71% accuracy but something went wrong and I am not able to replicate it. The model implemented now has accuracy of 31.06%.


