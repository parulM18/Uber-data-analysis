# Uber Travel-Time Data Analysis
## **Project Objective-**
To analyses the Uber Movement Data of New-Delhi and predict the time taken to travel from point A to point B.


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



#### 5. Wards with their centroids:


![image](https://user-images.githubusercontent.com/57316337/88228606-0e43c980-cc8d-11ea-8cb2-f2233d10cb1b.png)


Inference:
 - Every ward have a their centroid even the one which don't have ward-no. ans ward-name.
 
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
**mean_travel_time**: It is the mean time taken to travel from source to destination through all possible paths.\
**standard_deviation_travel_time**: It is the standard-deviation of the time taken to travel from source to destination though all possible paths. It tells about the variance of time taken to travel from various paths.\
**geometric_mean_travel_time**: For instance it is the mean time taken to travel from all points which are roughly the centroids of a ward A to all roughly centroid of ward B.\
**geometric_standard_deviation_travel_time**: It is the standard deviation of the geometric_mean_travel_time.\


- **Data description**:


![image](https://user-images.githubusercontent.com/57316337/88336166-27fb1480-cd52-11ea-8d4f-468853d723e7.png)


### Exploratory Data Analysis

 


