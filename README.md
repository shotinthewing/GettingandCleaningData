#Getting and Cleaning Data: Course Project

In this repository you can find all the files required for the project.

##The Data
The data used can be found here:

https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip 

A full description is available at the site where the data was obtained: 

http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphon

##The Files
*`CodeBook.md` is the file that describes the variables, the data, and any transformations or work performed to clean up the data.

*`run_analysis.R` is the R code that manipulates the data. What it does can be resumed in 5 steps: 
1) merges the training and the test sets to create one data set
2) extracts only the measurements on the mean and standard deviation for each measurement 
3) uses descriptive activity names to name the activities in the data set
4) appropriately labels the data set with descriptive variable names 
5) from the data set in step 4), creates a second, independent tidy data set with the average of each variable for each activity and each subject
The details on the manipulation of the data can be found as comments.

*`tidy.txt` is the final, tidy data set created in step 5)

