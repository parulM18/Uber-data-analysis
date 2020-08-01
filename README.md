# Uber Travel-Time Data Analysis
## **Project Objective-**
To analyses the Uber Movement Data of New-Delhi and predict the time taken to travel from point A to point B.
- The data is available on  https://movement.uber.com/
- Used NEW_DELHI_WARDS.JSON Data for analysing all the wards.
- Used 'Travel Times by Hour of Day (All Days)' for 2019 Quarter-2 for further analyses.

![image](https://user-images.githubusercontent.com/57316337/89111179-583c6480-d470-11ea-90ce-3a0ce56b3f15.png)


## Installation:
- pip install geopandas
- pip install shapely
- pip install pyproj

## 1. New-Delhi Wards Data
### Data Description:
- **Total Number of Rows**: 290
- **Total Number of Columns**: 5
- **Column Description**:


| Column        | Non-Null Count | Dtype     | Unique Values |
|  ------------ |--------------  |  -----    | ------------- |
| WARD_NO       | 289 non-null   |  object   | 289           | 
|  WARD_NAME    | 289 non-null   |  object   | 288           |
|  MOVEMENT_ID  | 290 non-null   |  object   | 290           |
|  DISPLAY_NAME | 290 non-null   |  object   | 290           |  
|  geometry     | 290 non-null   |  geometry | 290           |


**WARD_NO**: There is unique ward number assigned to every ward, here are 289 unique wards with 1 empty entry.\
**WARD_NAME**: Name of the particular ward, here are 288 unique wards with 1 empty entry.\
**MOVEMENT_ID**: Every ward has a unique movement-id which is same for every location of that particular ward.\
**DISPLAY_NAME**: Every ward has a unique Display name which is the proper name of that particular ward used to identify different locations.\
**geometry**: Geometry column displays the latitudes and longitudes of the wards.\
### Exploratory Data Analysis
#### 1. Plot of Delhi:


![image](https://user-images.githubusercontent.com/57316337/88227561-6d084380-cc8b-11ea-9a3e-19ac35e21d76.png)


#### 2. Visualising different wards(distinguished by MOVEMENT_ID):

![image](https://user-images.githubusercontent.com/57316337/88227962-0e8f9500-cc8c-11ea-9026-b9167bd93013.png)


#### 3. Visualising the wards on the basis of WARD_NO and locating the ward with empty value:

![image](https://user-images.githubusercontent.com/57316337/88228431-c9b82e00-cc8c-11ea-9dc4-0e3d950a5bb3.png)


Inference:
- The red coloured hatched lines represting the ward which don't have a Ward number.


#### 4. Visualising the wards on the basis of WARD_Name and locating the ward with empty value:


![image](https://user-images.githubusercontent.com/57316337/88228516-e81e2980-cc8c-11ea-8261-0baa07e48a0d.png)


Inferences:
 - The red coloured hatched lines represting the ward which don't have a Ward-Name.
 - This shows that the same ward have both the missing values i.e, of ward-no. and ward-name.
 - This unknown ward is some unnamed road in Shahdra Delhi.
 
 
 ![image](https://user-images.githubusercontent.com/57316337/88969688-d3661500-d2ce-11ea-9fc7-ce8594389d91.png)




#### 5. Wards with their centroids:


![image](https://user-images.githubusercontent.com/57316337/88228606-0e43c980-cc8d-11ea-8cb2-f2233d10cb1b.png)


Inference:
 - Every ward have their Latitude and longitude of centroid with respect to the lat-long of the geometry of the ward. Even the one which doesn't have the ward-no. and ward-name have their geometries.
 
 ## 2. New-delhi wards 2019(quater-2) All-Hourly-Aggregate data
 ### Data Description:
- **Total Number of Rows**: 1455932
- **Total Number of Columns**: 7
- **Column Description**:


Column                                    | Non-Null Count   | Dtype   | Unique Values |
----------------------------------------- | ---------------- |-------- | ------------- |                 
sourceid                                  | 1455932 non-null | int64   | 290           | 
dstid                                     | 1455932 non-null | int64   | 290           | 
hod                                       | 1455932 non-null | int64   | 24            |
mean_travel_time                          | 1455932 non-null | float64 | 419407        |
standard_deviation_travel_time            | 1455932 non-null | float64 | 126617        | 
geometric_mean_travel_time                | 1455932 non-null | float64 | 428278        |
geometric_standard_deviation_travel_time  | 1455932 non-null | float64 | 585           |


**sourceid**: It is the movement-id of a specific ward, whenever an Uber cab is booked at a specific source, a sourceid is assigned to it which is nothing but the movement id of that source(ward).\
**dstid**: dstid is associated with the destination, booked by the customer. A destination-id is assigned to every booked destination which is nothing but the movement-id of that destination(ward).\
**mean_travel_time**: It is the mean time(in seconds) taken to travel from source to destination through all possible paths.\
**standard_deviation_travel_time**: It is the standard-deviation of the time(in seconds) taken to travel from source to destination though all possible paths. It tells about the variance of time taken to travel from various paths.\
**geometric_mean_travel_time**: For instance it is the mean time(in seconds) taken to travel from all points which are roughly the centroids of a ward A to all roughly centroid of ward B.\
**geometric_standard_deviation_travel_time**: It is the standard deviation of the geometric_mean_travel_time(in seconds).\


- **Data description**:


![image](https://user-images.githubusercontent.com/57316337/88336166-27fb1480-cd52-11ea-8d4f-468853d723e7.png)


### Exploratory Data Analysis
#### Univariate Analysis
#### 1. Distribution of Sourceid and Dstid

 
![image](https://user-images.githubusercontent.com/57316337/88968394-e7a91280-d2cc-11ea-8c86-e0ceb28d296a.png) \
Blue- Indicates Sourceid\
Orange- Indicates Dstid


Inferences:
- Sourceid and Dstid have somewhat similar distribution. The reason for almost same count for both sourceid and dstid is because there are some places where people have gone and retured from there more often like the office area or some tourist spot etc, similarly for the less visited places so there the retured booking are also less.
- There are some peaks like from 0-20 and 60-70, this may be because these are the office area or the market place or tourist spots etc where people go and return more often.


#### 2. 'Hour of Day' distribution


![image](https://user-images.githubusercontent.com/57316337/88971595-d8789380-d2d1-11ea-99c3-fb882e684183.png)


Inferences:
- From 0 i.e, from 12-am to 3-am the number of uber booking keeps decreasing as these are the late-night hours, and then from 4-am it keeps increasing untill 12-noon because people started to travel for their offices and schools, colleges etc and after 12 the grapgh have almost maintains its peak like there have been a lot of booking through-out the day only after 8 or 9 it is slightly decreasing as people have already retured at their place.


#### 3. 'Mean travel time'distribution:


![image](https://user-images.githubusercontent.com/57316337/88972529-57ba9700-d2d3-11ea-8d3e-0f14d64465f2.png)


Inferences:
- The mean-travel-time for most of the places is approx half an hour(2000 sec.) and the maximum travel-time is approx 6000 sec. i.e, 1.6 hours.


#### 4. 'Standard-deviation-travel-time' distribution:


![image](https://user-images.githubusercontent.com/57316337/89069608-1688bc80-d391-11ea-9ce6-e666f7529bfc.png)


Inferences:
- The peak is at approx 8 mins(500 seconds) that means most of the cabs took 8 minutes more or less to cover the distance that the mean-travel-time.


### Bivariate analysis
#### 1. Average of mean-travel-time over the hours:


![image](https://user-images.githubusercontent.com/57316337/89054017-bcc6c900-d375-11ea-8ac7-40f15a8bd326.png)


Inferences:
- The average mean-travel-time varies all over the hours, at night it is the least because of the lesser traffic at this time, the uber bookings are also less at this time as seen stated earlier.
- Then the average time keeps increasing uptill 11 or 12 noon because of the increasing traffic and also increased number of bookings.
- After 12 noon the average travel-time is not constant although the number of bookings are almost constant as saw earlier, this is because at morning between 9am-12pm and in evening between 5pm-7pm the traffic is the most as this is the office arrival and departure time for most of the working people, so the average mean-travel-time also inreases with the traffic.


#### 2. Hour-of-day Vs mean-travel-time:


![image](https://user-images.githubusercontent.com/57316337/89055405-f0a2ee00-d377-11ea-8dfe-2034b4342dd1.png)


Inferences:
- The graph clearly shows the outliers at certain hours of the day, although it solely depends on the destination like how far the customer wants to travel.


#### 3. Hour-of-day Vs Standard-deviation-travel-time:


![image](https://user-images.githubusercontent.com/57316337/89073121-8306ba00-d397-11ea-993e-a4cdcb2a0f10.png)


Inferences:
- There are outliers at certain hours but again the standard-deviation doesn't depends on the hour of day, it siply shows that some uber cabs have taked significatly more or lesser time than the mean-travel-time taken for that particular destination.


#### 4. Mean-travel-time Vs Geometric-mean-travel-time


![image](https://user-images.githubusercontent.com/57316337/89073502-42f40700-d398-11ea-8e57-89fc3d6deef4.png)


Inferences:
Both Mean-travel-time and Geometric-mean-travel-time have a highly corelated linear relation between them, For instance if the geometric-mean-travel-time is the actual travel-time taken from the centroids of the wards then the mean-travel-time doesn't vary much with it.


### Pair Plot


![image](https://user-images.githubusercontent.com/57316337/89053957-a15bbe00-d375-11ea-8ca4-421c3ef6e301.png)


Inferences:
- This shows the exact relationship of each of the variables with each other.
- It tells about the outliers with respect to different variables, some of the important variables which i have used in my model have already been described above.


### Correlation:


![image](https://user-images.githubusercontent.com/57316337/89074565-2c4eaf80-d39a-11ea-8302-1aa6abd3ff0d.png)


![image](https://user-images.githubusercontent.com/57316337/89074598-3a9ccb80-d39a-11ea-89e0-043d7093a35e.png)


Inferences:
- Mean-travel-time and Geometric-mean-travel-time are highly correlated as already seen through the graphs.
- mean_travel_time, geometric_mean_travel_time, standard_deviation_travel_time are also slightly correlated with Hour-of-day, although the exact reason can't be stated for that.
- Although the sourceid and dstid have similar kind of distribution as shown earlier but they are not at all correlated with each other, because the place where customer wants to go i.e, the destination is nothing to do with his current location i.e, the source.
- geometric_mean_travel_time and geometric_standard_deviation_travel_time are the most non correlated here amongst all, simply because time-taken to travel and its standard deviation does not have any connection.


## Prepairing Data for Applying Model
- Joined the New-Delhi-ward data and Hourly-Aggregate-data such that in the final Data I have the information of sourceid and destinationid with their geometries, mean_travel_time between them according to the hour of day.


![image](https://user-images.githubusercontent.com/57316337/89111687-786f2200-d476-11ea-9bc4-be93b2494d27.png)


- Converted the multipoligon-geometry column of wards into the latitude and longitude of the centroid of every ward.

![image](https://user-images.githubusercontent.com/57316337/89111707-a81e2a00-d476-11ea-8b84-eb55bc72f724.png)


- Seperated the latitudes and longitudes of sourceid and dstid seperately so as to find the distance between lat-long of sourceid and lat-long of dstid.
- Calculated the distance between them using pyproj and from pyproj installing geod.


![image](https://user-images.githubusercontent.com/57316337/89111784-79548380-d477-11ea-856d-c79e183d8b08.png)


- Saved the final data in csv format.


![image](https://user-images.githubusercontent.com/57316337/89111740-0b0fc100-d477-11ea-967d-18668334834a.png)


- Independent variables:
 - Categorical variables- sourceid, dstid, HOD
 - Continuous variables- Distance in Km
- Dependent variable: mean_travel_time

## Applying Model
#### - Converted data into test and train


![image](https://user-images.githubusercontent.com/57316337/89111891-d997f500-d478-11ea-9e93-0015a8c15be6.png)


### - Applying RandomForestRegressor


![image](https://user-images.githubusercontent.com/57316337/89111905-1663ec00-d479-11ea-8c14-b37e6a4707d1.png)


### - Getting predicted values for mean_travel_time


![image](https://user-images.githubusercontent.com/57316337/89111928-7064b180-d479-11ea-8ef7-5f5741cdf0fa.png)


### - Accuracy:


![image](https://user-images.githubusercontent.com/57316337/89111940-c33e6900-d479-11ea-8439-3872c1968a86.png)

























