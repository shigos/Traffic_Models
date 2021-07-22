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

## Conclusion
