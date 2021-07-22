# Avoiding Auto Related Injuries

# Table of Contents
1. [Motivation](https://github.com/shigos/Traffic_Models/blob/main/README.md#motivation) 
2. [Data Description](https://github.com/shigos/Traffic_Models/blob/main/README.md#data-description)
3. [Cleaning/Notebooks](https://github.com/shigos/Traffic_Models/blob/main/README.md#data-description)
4. [EDA](https://github.com/shigos/Traffic_Models/blob/main/README.md#eda)
5. [Models](https://github.com/shigos/Traffic_Models/blob/main/README.md#modeling)
6. [Conclusion](https://github.com/shigos/Traffic_Models/blob/main/README.md#modeling)

### Motivation
There are over 30,000 auto fatal motor vechicle accidents each year in the United States alone.

The goal of this project is find trends and make inferences from the traffic accident data. In order improve safety, we should account all factors big and small. In this project I will be applying machine learning models to shed some light onto underlying factors that may contribute to injuries/death. The intention of finding these insights will lead us closer to factors which we can explore to improve saftey and prevent death.



## Data Description
The data was obtained from the city of Chicago's data portal. 
This data was collected by the Chicago Police Department and spans from 2015 to 2021 (Although the data set is being updated daily) 
The entire dataset is comprised of three csv files [https://data.cityofchicago.org/Transportation/Traffic-Crashes-Crashes/85ca-t3if]

Traffic Crash.csv - 522K rows 49 Columns \
Traffic People.csv - 1.15M rows 30 Columns\
Traffic Vehicle.csv - 1.07M rows 72 Columns

The traffic CRASH_RECORD_ID is used to link the same crash between crashes in the Vehicles and People datasets

## Cleaning/Notebooks 
Given the large amount of data in this project I decided to start by cleaning data in the individual csv files. Three notebooks were created using the original csv titles as the notebook title. A notebook titled full_note.ipynb contains the initial join of the three raw data frames before cleaning. Missing and nan values were filled using with "Unknown" and "Nans" represented by 0. Columns which classified a binary outcome were filled accordingly and missing values were considered 0. Cleaning was done individually to each individual csv files. Upon joining the three "cleaned" data sets on CRASH_RECORD_ID a new data frame was created which was named clean_merge_note which contains most of the eda and modeling information in this project. A target using INJURIES_TOTAL column was feature engineered for determining whether the crash resulted in injury.

A copy was made to make the initial model which was used as a baseline in clean_merge_note1.
full_note contains initial eda prior to cleaning.
fatal_eda contains information contains initial eda prior to cleaning with fatal crashes isolated for data exploration.

## EDA

![fatal_map_plot](https://user-images.githubusercontent.com/76585249/126579407-961a1fd3-4ec8-4419-8d52-303f3fa6b2b0.png)

The EDA shows that fatal accidents have a rate of occcurence in certain districts. Further investigation into enviornmental factors would be required to determine causation.
The graph below shows a bar graph of the occurences of crashes in the entire dataframe both fatal and non fata.
It seems that despite district 8 being the location where most crashes are occuring, there is a reason not yet discovered resulting in the higher number of fatal crashes in districts 11 and 1 shown in the graph. 
![districts ](https://user-images.githubusercontent.com/76585249/126584127-f1af04cf-747e-4094-adc9-c61d805f1ec1.png)

Graph above shows district of crash occurrence of overall data set.

![fatal month](https://user-images.githubusercontent.com/76585249/126584115-48e2d7e1-1252-4a26-84cc-33dbcff54a14.png)

May shows disproportionately higher fatal accidents than other months even of the same season. Of the total fatal crashes in the data, 19% of all fatal crashes occured in May. 

Initially the target was chosen based off of fatal accidents. Given the limited amount of time, this was altered to reflect injuries resulting from the crash.

![Hourly crash](https://user-images.githubusercontent.com/76585249/126584121-7ea707ec-7ba3-413b-a285-bc32f1ad184f.png)

The time frame that encompases afternoon rush hour shows the largest number of crash occurences. The large number of accidents occuring at this time approprately corresponds to the number of cars on the road during peak traffic hours.


## Modeling
Modeling was done first with Logistic Regression and a subsample of 10,000 rows and 10 features. This is shown in the clean_note_copy version of the notebook. Models using Random Forest as well as Gradient Boosted Trees were implemented with results only slightly improved from the first model. Due to the presence of class a class imbalance of target class(crashes resulting in injury) a balanced sample was taken for model comparison. A equal number of samples were taken using a random method without for model training. This was tested against a randomly sampled data of the skewed data from the original data set. 

Graphs below shows the first model used with no paramater tuning: 10k rows and 10 features

![log first](https://user-images.githubusercontent.com/76585249/126593074-b8d5e98d-eeec-49eb-b3db-d3ea7df15592.png)  


| Random Forest ROC | Random Forest Precision |
| ------------- | ------------- |
| ![random forest first(2)](https://user-images.githubusercontent.com/76585249/126593279-bcd1b1c6-608a-4425-bcc2-5f2c134aa282.png)   | ![random forest first](https://user-images.githubusercontent.com/76585249/126593422-092550e9-0b6c-4aac-8822-41ad9a91da03.png)
 |







## Conclusion
Drawing feature importances, I used a combination of shapely values as well as coeficcients from the best performing models. Although the many of the feature importances contributing to crash injury seemed obvious such as "Following too closely", "Airbag Deployment" and "Driver's Physical Condition". Other not so apparent features that I found based off my findings included "District 11" and "Trafficway- Parkinglot". Although the determinant factor is not explicit, I can infer that this is most likely due to envornmental reasons. For those looking to address this I would advise looking at road infrastructure/layouts , road conditions, and street signage for possible faults.
