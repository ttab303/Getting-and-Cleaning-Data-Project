# Getting-and-Cleaning-Data-Project

##Course Projet

###You should create one R script called run_analysis.R that does the following.

1- Merges the training and the test sets to create one data set.

2- Extracts only the measurements on the mean and standard deviation for each measurement.

3- Uses descriptive activity names to name the activities in the data set

4- Appropriately labels the data set with descriptive variable names.

5- From the data set in step 4, creates a second, independent tidy data set with the average of each variable for each activity and each     subject.

###Code

subject_train <- read.table("train/subject_train.txt")
subject_test <- read.table("test/subject_test.txt")

X_train <- read.table("train/X_train.txt")
y_train <- read.table("train/y_train.txt")

X_test <- read.table("test/X_test.txt")
y_test <- read.table("test/y_test.txt")

# add column name for subject files
names(subject_train) <- "subjectID"
names(subject_test) <- "subjectID"

# add column names for measurement files
featureNames <- read.table("features.txt")

names(X_train) <- featureNames$V2
names(X_test) <- featureNames$V2

# add column name for label files
names(y_train) <- "activity"
names(y_test) <- "activity"

# combine files into one dataset
All_train <- cbind(subject_train, y_train, X_train)
All_test <- cbind(subject_test, y_test, X_test)

Train_test <- rbind(All_train, All_test)



##Steps to work on this course project

Download the data source and put into a folder on your local drive. You'll have a UCI HAR Dataset folder.
Put run_analysis.R in the parent folder of UCI HAR Dataset, then set it as your working directory using setwd() function in RStudio.
Run source("run_analysis.R"), then it will generate a new file tidy.txt in your working directory.


