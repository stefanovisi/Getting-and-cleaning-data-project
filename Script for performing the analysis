#Project##########################################
#In this script all steps undertaken in order to follow the project instruction are recorded and described.

#I set up a working directory 
setwd ("C:/Users/stefano/Dropbox/cursera/Getting and cleaning/project/")

#Open the Train and Test datasets
train <- read.table("./UCI HAR Dataset/train/X_train.txt")
test <- read.table("./UCI HAR Dataset/test/X_test.txt")
#Load and append the label variables to each dataset
ltrain <- read.table("./UCI HAR Dataset/train/y_train.txt")
ltest <- read.table("./UCI HAR Dataset/test/y_test.txt")
strain <- read.table("./UCI HAR Dataset/train/subject_train.txt")
stest <- read.table("./UCI HAR Dataset/test/subject_test.txt")
train$class <- ltrain[,1]
test$class <- ltest[,1]
train$subject <- strain[,1]
test$subject <- stest[,1]
#load features names
names <- read.table("./UCI HAR Dataset/features.txt")

#1.Merges the training and the test sets to create one data set.
ds <- rbind(train,test)
colnames(ds)[1:561] <- as.vector(names[,2])#assign names to columns
rm(train, test, names, ltest, ltrain, strain, stest)

#2. Extracts only the measurements on the mean and standard deviation for each measurement.
ds <- ds[ , grepl("-mean()" , names( ds ) ) | grepl("std" , names( ds )) | grepl ("class", names(ds)) |grepl ("subject", names(ds) ) ]

#3. Uses descriptive activity names to name the activities in the data set
#actnames <- read.table("./UCI HAR Dataset/activity_labels.txt")
ds$class_names[ds$class == 1] <- "WALKING"
ds$class_names[ds$class == 2] <- "WALKING_UPSTAIRS"
ds$class_names[ds$class == 3] <- "WALKING_DOWNSTARIS"
ds$class_names[ds$class == 4] <- "SITTING"
ds$class_names[ds$class == 5] <- "STANDING"
ds$class_names[ds$class == 6] <- "LAYING"
#rm(actnames)

#4. Appropriately labels the data set with descriptive variable names. 
#This step has been already undertaken while steps 1 to 3.

#I save the dataset as a csv file
write.csv(ds,"tydy_ds1.csv")


#5. From the data set in step 4, creates a second, independent tidy data set with the average of each variable for each activity and each subject.
ds$class_names <- factor(ds$class_names)
ds$subject <- factor(ds$subject)

library(reshape)
Molten <- melt(ds, id.vars = c("class_names", "subject"))
Molten[1:10,]
ds2 <- cast(class_names + subject ~ variable, data = Molten, fun = mean)

#I save this second dataset as a csv file
write.csv(ds2,"tydy_ds2.csv")
