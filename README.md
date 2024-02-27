# AI-Project-6th-Semester-
Method:
1.We first filtered the data and created new csv files to store them.
2.We replaced the Date and Time columns with 144 time slots for the entire day.
3.From the region file, we obtained a dataset with region hash and corresponding region ids. We created a dictionary of this and replaced all the region hash with region ids in all files.
4.We merged the order, poi, and weather data into a single dataset.
5.We converted the date-time slot format and deleted the extra columns.
6.We grouped the data by TimeSlot(tj) and Region_hash and aggregated all columns.
7.We renamed the columns of demand and supply and created a new column "gap(ij)" that represents the demand-supply gap.
8.Since the data was too big, we only took a subset for further analysis.
9.We used four different models to predict the demand-supply gap using the rolling window approach.
10.We trained and tested these models on the training and testing datasets.
11.For each model, we iterated through the dataset using a window of size 6, fitted the model on each window, and made a prediction for the next data point. We then evaluated the model on the test dataset using mean absolute error.
12.We compared the mean absolute error of all the models and selected the one with the lowest error as our final model.
Choosing the Features:
Demand(rij), Supply(aij), and gap(ij) were not used as features, as they are the target variables, or used directly in creating the target variable, that we want to predict. Including them as features would lead to data leakage. Similarly, timeSlot(tj) and Region_hash were also not included in features because the Demand(rij) and Supply(aij) were aggregated on their basis, along with other features.
Weather: Weather conditions at the time of the ride can affect the demand for rides.
Temperature: Temperature can also affect the demand for rides, especially in extreme weather conditions as it impacts the comfort level of riders.
Humidity: Humidity is another environmental factor that can impact the demand for rides, especially in tropical regions where it is high. High humidity levels can make the weather feel hotter and stickier, leading to lower demand for rides.
POI_Class_Count: The number of different facilities in a region could affect the demand for rides. Regions with more facilities, such as shopping centers, could potentially have higher demand for rides.
POI_Class: The type of facilities in a region could also affect the demand for rides. For instance, regions with more entertainment facilities could have a higher demand for rides during weekends. The specific types of facilities can provide insights into the demand patterns.
