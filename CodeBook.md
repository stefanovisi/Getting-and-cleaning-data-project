Codebook
Summary
The purpose of this codebook is to provide information on the datasets provided. First, all data processing steps are described from row data to the two final datasets. Data have been collected within experiment on human activities and processed according to the instructions received. Subjects performed 6 different activities (WALKING, WALKING_UPSTAIRS, WALKING_DOWNSTAIRS, SITTING, STANDING, LAYING) while wearing an accelerometer and a gyroscope. Raw data are processed according to a 5 point list of instruction received.
Datasets
Two datasets are provided: 
tydy_ds1.txt
tydy_ds2.txt
In tydy_ds1.txt training and test raw dataset are merged. Only information on mean and standard deviation for each measurement are extracted. Variable names are set according to the following principles:
t represents time
f represents frequencies
Acc stays for accelerometer signal
Gyroscope for the gyroscope signal
 class and class_names are the activity labels
subject is the id variable distinguishing the 30 subject who took part in the project
In tydy_ds2.txt each variable is the average of each variable in tydy_ds1.txt for each activity and each subject.


Data processing
In order to obtain the datasets provided the following operations had been implemented.
Raw data were obtained tat the following link:
https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip 
X_train.txt and X_test.txt files were loaded. Class (y_train.txt; y_test.txt) and subject (subject_train.txt ; subject_test.txt) labels were loaded and appended to the corresponding dataframes. Features names were loaded (features.txt).
Train and test dataframes were merged and features names were assigned to the corresponding variables.
For each measurement provided within the original data, only mean and standard deviation were extracted, as well as subject-id and class variables.
The original descriptive names were used to label variables and the dataset was saved as tydy_ds1.txt .
Furthermore a second dataset has been created. The mean of each of the variables of the first dataset has been computed for each individual and activity performed. The second dataset has been saved as tydy_ds2.txt . 
