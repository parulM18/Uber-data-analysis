# Uber Travel-Time Data Analysis
## Project Objective-
To analyses the Uber Movement Data of New-Delhi and predict the time taken to travel from point A to point B.


### **1. New-Delhi Wards Data**
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
**MOVEMENT_ID**: Every ward have a unique movement-id which is same for every location of that particular ward.\
**DISPLAY_NAME**: Every ward have a unique Display name which is the proper name of that particular ward used to identify different locations.\
**geometry**: Geometry column displays the latitudes and longitudes of the wards.\
### Exploratory Data Analysis
1. Plot of Delhi:


![image](https://user-images.githubusercontent.com/57316337/88227561-6d084380-cc8b-11ea-9a3e-19ac35e21d76.png)


2. Visualising different wards(distinguished by MOVEMENT_ID):

![image](https://user-images.githubusercontent.com/57316337/88227962-0e8f9500-cc8c-11ea-9026-b9167bd93013.png)


3. Visualising the wards on the basis of WARD_NO and locating the ward with empty value:

![image](https://user-images.githubusercontent.com/57316337/88228431-c9b82e00-cc8c-11ea-9dc4-0e3d950a5bb3.png)
#### Inferences:
- The red coloured hatched lines represting the ward which don't have a Ward number.

4. Visualising the wards on the basis of WARD_Name and locating the ward with empty value:


![image](https://user-images.githubusercontent.com/57316337/88228516-e81e2980-cc8c-11ea-8261-0baa07e48a0d.png)
#### Inferences:
- The red coloured hatched lines represting the ward which don't have a Ward-Name.

5. Wards with their centroids:

![image](https://user-images.githubusercontent.com/57316337/88228606-0e43c980-cc8d-11ea-8cb2-f2233d10cb1b.png)




