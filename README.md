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


















