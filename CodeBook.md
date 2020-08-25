---
title: "CodeBook.m"
author: "JMVergara"
date: "24/8/2020"
output: html_document
---

The run_analysis.R script performs the data preparation and then followed by the 5 steps required as described in the course project’s definition.

## The Data:
The data are obtained from next link:

https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip

The dataset includes the following files:
  - 'README.txt'

  - 'features_info.txt': Shows information about the variables used on the feature vector.

  - 'features.txt': List of all features.

  - 'activity_labels.txt': Links the class labels with their activity name.

  - 'train/X_train.txt': Training set.

  - 'train/y_train.txt': Training labels.

  - 'test/X_test.txt': Test set.

  - 'test/y_test.txt': Test labels.

The following files are available for the train and test data. Their descriptions are equivalent.

  - 'train/subject_train.txt': Each row identifies the subject who performed the activity for each window sample. Its range is from 1 to 30.

  - 'train/Inertial Signals/total_acc_x_train.txt': The acceleration signal from the smartphone accelerometer X axis in standard gravity units 'g'. Every row shows a 128 element vector. The same description applies for the 'total_acc_x_train.txt' and 'total_acc_z_train.txt' files for the Y and Z axis.

  - 'train/Inertial Signals/body_acc_x_train.txt': The body acceleration signal obtained by subtracting the gravity from the total acceleration.

  - 'train/Inertial Signals/body_gyro_x_train.txt': The angular velocity vector measured by the gyroscope for each window sample. The units are radians/second.

Assign each data to variables:

  - features <- features.txt : 561 rows, 2 columns
The features selected for this database come from the accelerometer and gyroscope 3-axial raw signals tAcc-XYZ and tGyro-XYZ.

  - activities <- activity_labels.txt : 6 rows, 2 columns
List of activities performed when the corresponding measurements were taken and its codes (labels)

  - subject_test <- test/subject_test.txt : 2947 rows, 1 column
contains test data of 9/30 volunteer test subjects being observed

  - x_test <- test/X_test.txt : 2947 rows, 561 columns
contains recorded features test data

  - y_test <- test/y_test.txt : 2947 rows, 1 columns
contains test data of activities’code labels

  - subject_train <- test/subject_train.txt : 7352 rows, 1 column
contains train data of 21/30 volunteer subjects being observed

  - x_train <- test/X_train.txt : 7352 rows, 561 columns
contains recorded features train data

  - y_train <- test/y_train.txt : 7352 rows, 1 columns
contains train data of activities’code labels

Merges the training and the test sets to create one data set
  - X (10299 rows, 561 columns) is created by merging x_train and x_test using rbind() function
  - Y (10299 rows, 1 column) is created by merging y_train and y_test using rbind() function
  - Subject (10299 rows, 1 column) is created by merging subject_train and subject_test using rbind() function
  - all_data(10299 rows, 563 column) is created by merging Subject, Y and X using cbind() function

Extracts only the measurements on the mean and standard deviation for each measurement
tidy_data (10299 rows, 88 columns) is created by subsetting Merged_Data, selecting only columns: subject, code and the measurements on the mean and standard deviation (std) for each measurement

Uses descriptive activity names to name the activities in the data set
Entire numbers in code column of the TidyData replaced with corresponding activity taken from second column of the activities variable

Appropriately labels the data set with descriptive variable names
code column in TidyData renamed into activities
  - All Acc in column’s name replaced by Accelerometer
  - All Gyro in column’s name replaced by Gyroscope
  - All BodyBody in column’s name replaced by Body
  - All Mag in column’s name replaced by Magnitude
  - All start with character f in column’s name replaced by Frequency
  - All start with character t in column’s name replaced by Time

From the data set in step 4, creates a second, independent tidy data set with the average of each variable for each activity and each subject

  - final_tidy_data (180 rows, 88 columns) is created by sumarizing tidy_data taking the means of each variable for each activity and each subject, after groupped by subject and activity.
  
Export final_tidy_data into "tidy_data.txt" file.
