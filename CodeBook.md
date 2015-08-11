#Description

The file `run_analysis` performs the analysis of the [data] (https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip )
required by the project assignment, consisting in the 5 steps listed in the `README.md` file. The analysis returns a data set
called `tidy.txt` containing the average of the measured variable over two identifiers: _Subject_ and _Activity_.

#Variables:
(complete list from the file `feature.txt`. Details about the measurements can be found in the file 'features_info.txt'. Both files are contained in the data folder)

* _tBodyAcc-mean()-X_           
* _tBodyAcc-mean()-Y_          
* _tBodyAcc-mean()-Z_           
* _tBodyAcc-std()-X_            
* _tBodyAcc-std()-Y_            
* _tBodyAcc-std()-Z_           
* _tGravityAcc-mean()-X_        
* _tGravityAcc-mean()-Y_        
* _tGravityAcc-mean()-Z_        
* _tGravityAcc-std()-X_        
* _tGravityAcc-std()-Y_         
* _tGravityAcc-std()-Z_         
* _tBodyAccJerk-mean()-X_       
* _tBodyAccJerk-mean()-Y_      
* _tBodyAccJerk-mean()-Z_       
* _tBodyAccJerk-std()-X_       
* _tBodyAccJerk-std()-Y_        
* _tBodyAccJerk-std()-Z_       
* _tBodyGyro-mean()-X_          
* _tBodyGyro-mean()-Y_          
* _tBodyGyro-mean()-Z_          
* _tBodyGyro-std()-X_          
* _tBodyGyro-std()-Y_           
* _tBodyGyro-std()-Z_           
* _tBodyGyroJerk-mean()-X_      
* _tBodyGyroJerk-mean()-Y_     
* _tBodyGyroJerk-mean()-Z_      
* _tBodyGyroJerk-std()-X_      
* _tBodyGyroJerk-std()-Y_       
* _tBodyGyroJerk-std()-Z_      
* _tBodyAccMag-mean()_          
* _tBodyAccMag-std()_          
* _tGravityAccMag-mean()_       
* _tGravityAccMag-std()_       
* _tBodyAccJerkMag-mean()_      
* _tBodyAccJerkMag-std()_      
* _tBodyGyroMag-mean()_       
* _tBodyGyroMag-std()_        
* _tBodyGyroJerkMag-mean()_     
* _tBodyGyroJerkMag-std()_     
* _fBodyAcc-mean()-X_           
* _fBodyAcc-mean()-Y_          
* _fBodyAcc-mean()-Z_           
* _fBodyAcc-std()-X_            
* _fBodyAcc-std()-Y_            
* _fBodyAcc-std()-Z_           
* _fBodyAccJerk-mean()-X_       
* _fBodyAccJerk-mean()-Y_       
* _fBodyAccJerk-mean()-Z_       
* _fBodyAccJerk-std()-X_       
* _fBodyAccJerk-std()-Y_        
* _fBodyAccJerk-std()-Z_        
* _fBodyGyro-mean()-X_          
* _fBodyGyro-mean()-Y_         
* _fBodyGyro-mean()-Z_          
* _fBodyGyro-std()-X_           
* _fBodyGyro-std()-Y_           
* _fBodyGyro-std()-Z_          
* _fBodyAccMag-mean()_          
* _fBodyAccMag-std()_           
* _fBodyBodyAccJerkMag-mean()_  
* _fBodyBodyAccJerkMag-std()_  
* _fBodyBodyGyroMag-mean()_     
* _fBodyBodyGyroMag-std()_      
* _fBodyBodyGyroJerkMag-mean()_ 
* _fBodyBodyGyroJerkMag-std()_

#Identifiers:
__Subject__: 30 different individuals

__Activity__:
(from the file `activity_labels.txt` contained in the data folder)
* _WALKING_
* _WALKING_UPSTAIRS_
* _WALKING_DOWNSTAIRS_
* _SITTING_
* _STANDING_
* _LAYING_

#Manipulation of the data
##Step1:
data from from the `train` and `test` folder are merged. We read the data contained in `train/X_train.txt` and `test/X_train.txt` and use the function __rbind()__ to put them together. We do the same for the `y` and `subject` data sets. In the end we __cbind()__ the `X`, `y` and `subject` merged data sets to get the `fulldata` data frame.

##Step2:
we use the __grep()__ function to extract from the file containing the list of activities, `features.txt`, the features we are interested in and filter the data containing measurements of means and standard deviations, that we put in a data frame called `mean_std`.

##Step3:
we read the activity names from `activity_labels.txt` to substitute them to the corresponding numbers in the `y` data.

##Step4:
we give the variable name `Subject` to the subject data frame. Then, we create the clean data frame containing all the appropriate variable names, `cleanset`.

##Step5:
We load the R library __reshape2__ since we need the functions __melt()__ and __dcast()__. We melt `cleanset` with identifiers `Subject` and `Activity` and then we average the other variables using __mean__ inside the __dcast()__ function. We call the final data frame ´finalset´ and we write it in the output `tidy.txt`.
