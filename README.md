# Avoiding Auto Related Injuries

# Table of Contents
1. [Motivation](https://github.com/shigos/Traffic_Models/blob/main/README.md#motivation) 
2. [Data Description](https://github.com/shigos/Traffic_Models/blob/main/README.md#data-description)
3. [Cleaning/Notebooks](https://github.com/shigos/Traffic_Models/blob/main/README.md#data-description)
4. [EDA](https://github.com/shigos/Traffic_Models/blob/main/README.md#eda)
5. [Models]()
### Motivation
There are over 30,000 auto fatal motor vechicle accidents each year in the United States alone.

The goal of this project is find some trends and make inferences from the traffic accident data. In order improve safety, we must address all factors big and small. The purpose of applying machine learning is to hopefully shed some light onto underlying factors that may contribute to injuries/death. 



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
The 
![fatal_map_plot](https://user-images.githubusercontent.com/76585249/126579407-961a1fd3-4ec8-4419-8d52-303f3fa6b2b0.png)
