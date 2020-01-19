## A BRIEF DESCRIPTION OF THE PROCESS:

# About the data

- The data obtained from Samsung Data was found in the following order:

- On the UCI HAR Folder:

On the train folder:

1. subject_train.txt: One file containing the numeric tag for the subject performing the excercises (1,2,3,4...up to 30).
2. X_train.txt: One file containing the numeric tag for the activity being performed (1,2,3,4,5,6).
3. y_train.txt: One file containing the raw data of each variable measured/computed during the experiment.

On the test folder:

4. subject_test.txt: One file containing the numeric tag for the subject performing the excercises (1,2,3,4...up to 30).
5. X_test.txt: One file containing the numeric tag for the activity being performed (1,2,3,4,5,6).
6. y_test.txt: One file containing the raw data of each variable measured/Computed during the experiment.

Additionally, on the UCI HAR folder data on activity names (activity_labels.txt) and features (features.txt) were imported. 

# Reading the data

- Therefore, the eight files or dataset read into R using the command read.table(), and are as follows in R:

1. subject_train.txt: imported as TrainingData_subject (integer of 7352 obs).
2. X_train.txt: imported as TrainingData_xtest (numeric values of 7352 obs and 561 variables).
3. y_train.txt: imported as TrainingData_ytest (integer of 7352 obs).
4. subject_test.txt: imported as TestData_subject (integer of 2947 obs).
5. X_test.txt: imported as TestData_xtest (numeric values of 2947 obs and 561 variables).
6. y_test.txt: imported as TestData_ytest (integer of 2947 obs).
7. activity_labels.txt: imported as Activity_labels ( 6 obs of 1 variable (character values like "STANDING","WALKING",etc...)).
8. features.txt: imported as Features (561 obs of 1 variable (character values like "tBodyAcc-mean()-X","tBodyAcc-mean()-Y", and so on)).

# Merging Dataset

- Data imported was merged using cbind() and rbind() functions, as follows:

1. Test data was merged using cbind() operator (TestData dataframe in R).
2. Training data was merged using cbind() operator (TrainingData dataframe in R).
3. Preliminary merged dataset was merged (from test and training data) using rbind() operator (MergedDataset dataframe in R).

# Naming columns (variables) names

- A vector of variables names was prepared from the Features variable (or Features.txt file) using colnames() function and assigned to
a preliminary merged dataset (MergedDataset dataframe in R).

# Extracting mean and standard deviation from each measurement

- A smaller dataset was extracted from MergedDataset dataframe using the function grep() with arguments "mean()" and "std()".
- The subsetting was done using x[,criteria] sort of command. where criteria is the output from grep() function.
- The smaller dataset is saved as MergeData dataframe in R.
 
 # Naming activities in the dataset
 
- To name the acivities of the dataset using the activities names from the file activity_labels.txt, we used a user-defined function called Rename_rows() that looks up the Activity index from MergedData variable (second column), and gets the activity name associated in the Activity_labels dataframe defined in R. This is similar to applying a Vlookup function in excel.
 
- The output (character vector with the activity names) was appended as a column in the dataset using cbind() and the dataset. The new dataframe named as FinalMergedData in R.

# Consolidating dataset as a tidy dataset

- An intermediate step was scripted, to purge unwanted columns that got in the dataset from applying the grep() function, mainly of name  meanFreq(). The dataset is saved as a dataframe named StatsData.

# Producing average of each variable in the tidy dataset

- Using dplyr package, we produce the averages of each column, using the group_by() and summarise_all() functions from the package.
- In this process we report the average by activity and by subject, in that order.
- We reorganize the dataset, using the arrange() command of dplyr package, the final dataframed being saved as TidyData in R.
 
 # Exporting the dataset
 - We export the Tidy dataset using write.table() command.
 

The TidyDataset obtained from this process, contains the following information extracted from the Samsung Data files

1  Subject: Tag of each individual who performed the excercises

2  Activity_names: Names of the activities performed by each individual

3  Activity: Tag for each activity performed by each individual

4  tBodyAcc-mean()-X: Mean of body accelaration in the X direction in the time domain, (standard gravity units, 'g')

5  tBodyAcc-mean()-Y: Mean of body accelaration in the Y direction in the time domain, (standard gravity units, 'g')

6  tBodyAcc-mean()-Z: Mean of body accelaration in the Z direction in the time domain, (standard gravity units, 'g')

7  tBodyAcc-std()-X: Standard deviation of body accelaration in the X direction in the time domain, (standard gravity units, 'g')

8  tBodyAcc-std()-Y: Standard deviation of body accelaration in the Y direction in the time domain, (standard gravity units, 'g')

9  tBodyAcc-std()-Z: Standard deviation of body accelaration in the Z direction in the time domain, (standard gravity units, 'g')

10 tGravityAcc-mean()-X: Mean of gravity acceleration in the X direction in the time domain, (standard gravity units, 'g')

11 tGravityAcc-mean()-Y: Mean of gravity acceleration in the Y direction in the time domain, (standard gravity units, 'g')

12 tGravityAcc-mean()-Z: Mean of gravity acceleration in the Z direction in the time domain, (standard gravity units, 'g')

13 tGravityAcc-std()-X: Standard deviation of gravity acceleration in the X direction in the time domain, (standard gravity units, 'g')

14 tGravityAcc-std()-Y: Standard deviation of gravity acceleration in the Y direction in the time domain, (standard gravity units, 'g')

15 tGravityAcc-std()-Z: Standard deviation of gravity acceleration in the Z direction in the time domain, (standard gravity units, 'g')

16 tBodyAccJerk-mean()-X: Mean of Jerk signal of body acceleration in the X direction in the time domain, (standard gravity units, 'g')

17 tBodyAccJerk-mean()-Y: Mean of Jerk signal of body acceleration in the Y direction in the time domain, (standard gravity units, 'g')

18 tBodyAccJerk-mean()-Z: Mean of Jerk signal of body acceleration in the Z direction in the time domain, (standard gravity units, 'g')

19 tBodyAccJerk-std()-X: Standard deviation of Jerk signal of body acceleration in the X direction in the time domain, (standard gravity units, 'g')

20 tBodyAccJerk-std()-Y: Standard deviation of Jerk signal of body acceleration in the Y direction in the time domain, (standard gravity units, 'g')

21 tBodyAccJerk-std()-Z: Standard deviation of Jerk signal of body acceleration in the Z direction in the time domain, (standard gravity units, 'g')

22 tBodyGyro-mean()-X: Mean of body angular velocity in the X direction in the time domain, (radians/second)

23 tBodyGyro-mean()-Y: Mean of body angular velocity in the Y direction in the time domain, (radians/second)

24 tBodyGyro-mean()-Z: Mean of body angular velocity in the Z direction in the time domain, (radians/second)

25 tBodyGyro-std()-X: Standard deviation of body angular velocity in the X direction in the time domain, (radians/second)

26 tBodyGyro-std()-Y: Standard deviation of body angular velocity in the Y direction in the time domain, (radians/second)

27 tBodyGyro-std()-Z: Standard deviation of body angular velocity in the Z direction in the time domain, (radians/second)

28 tBodyGyroJerk-mean()-X: Mean of Jerk signal of body angular velocity in the X direction in the time domain, (radians/second)

29 tBodyGyroJerk-mean()-Y: Mean of Jerk signal of body angular velocity in the Y direction in the time domain, (radians/second)

30 tBodyGyroJerk-mean()-Z: Mean of Jerk signal of body angular velocity in the Z direction in the time domain, (radians/second)

31 tBodyGyroJerk-std()-X: Standard deviation of Jerk signal of body angular velocity in the X direction in the time domain, (radians/second)

32 tBodyGyroJerk-std()-Y: Standard deviation of Jerk signal of body angular velocity in the Y direction in the time domain, (radians/second)

33 tBodyGyroJerk-std()-Z: Standard deviation of Jerk signal of body angular velocity in the Z direction in the time domain, (radians/second)

34 tBodyAccMag-mean(): Mean of magnitude of body acceleration in the time domain, (standard gravity units, 'g')

35 tBodyAccMag-std(): Standard deviation of magnitude of body acceleration in the time domain, (standard gravity units, 'g')

36 tGravityAccMag-mean(): Mean of magnitude of gravity acceleration in the time domain, (standard gravity units, 'g')

37 tGravityAccMag-std(): Standard deviation of magnitude of gravity acceleration in the time domain, (standard gravity units, 'g')

38 tBodyAccJerkMag-mean(): Mean of magnitude of Jerk signal of body acceleration in the time domain, (standard gravity units, 'g')

39 tBodyAccJerkMag-std(): Standard deviation of magnitude of Jerk signal of body acceleration in the time domain, (standard gravity units, 'g')

40 tBodyGyroMag-mean(): Mean of magnitude of body angular velocity in the time domain, (radians/second)

41 tBodyGyroMag-std(): Standard deviation of magnitude of body angular velocity in the time domain, (radians/second)

42 tBodyGyroJerkMag-mean(): Mean of magnitude of Jerk signal of body angular velocity in the time domain, (radians/second)

43 tBodyGyroJerkMag-std(): Standard deviation of magnitude of Jerk signal of body angular velocity in the time domain, (radians/second)

44 fBodyAcc-mean()-X: Mean of body acceleration in the X direction in the frequency domain, (standard gravity units, 'g')

45 fBodyAcc-mean()-Y: Mean of body acceleration in the Y direction in the frequency domain, (standard gravity units, 'g')

46 fBodyAcc-mean()-Z: Mean of body acceleration in the Z direction in the frequency domain, (standard gravity units, 'g')

47 fBodyAcc-std()-X: Standard deviation of body acceleration in the X direction in the frequency domain, (standard gravity units, 'g')

48 fBodyAcc-std()-Y: Standard deviation of body acceleration in the Y direction in the frequency domain, (standard gravity units, 'g')

49 fBodyAcc-std()-Z: Standard deviation of body acceleration in the Z direction in the frequency domain, (standard gravity units, 'g')

50 fBodyAccJerk-mean()-X: Mean of Jerk signal of body acceleration in the X direction in the frequency domain, (standard gravity units, 'g')

51 fBodyAccJerk-mean()-Y: Mean of Jerk signal of body acceleration in the Y direction in the frequency domain, (standard gravity units, 'g')

52 fBodyAccJerk-mean()-Z: Mean of Jerk signal of body acceleration in the Z direction in the frequency domain, (standard gravity units, 'g')

53 fBodyAccJerk-std()-X: Standard deviation of Jerk signal of body acceleration in the X direction in the frequency domain, (standard gravity units, 'g')

54 fBodyAccJerk-std()-Y: Standard deviation of Jerk signal of body acceleration in the Y direction in the frequency domain, (standard gravity units, 'g')

55 fBodyAccJerk-std()-Z: Standard deviation of Jerk signal of body acceleration in the Z direction in the frequency domain, (standard gravity units, 'g')

56 fBodyGyro-mean()-X: Mean of body angular velocity in the X direction in the frequency domain, (radians/second)

57 fBodyGyro-mean()-Y: Mean of body angular velocity in the Y direction in the frequency domain, (radians/second)

58 fBodyGyro-mean()-Z: Mean of body angular velocity in the Z direction in the frequency domain, (radians/second)

59 fBodyGyro-std()-X: Standard deviation of body angular velocity in the X direction in the frequency domain, (radians/second)

60 fBodyGyro-std()-Y: Standard deviation of body angular velocity in the Y direction in the frequency domain, (radians/second)

61 fBodyGyro-std()-Z: Standard deviation of body angular velocity in the Z direction in the frequency domain, (radians/second)

62 fBodyAccMag-mean(): Mean of magnitude of body acceleration in the frequency domain, (standard gravity units, 'g')

63 fBodyAccMag-std(): Standard deviation of magnitude of body acceleration in the frequency domain, (standard gravity units, 'g')

64 fBodyBodyAccJerkMag-mean(): Mean of magnitude of Jerk signal of body acceleration in the frequency domain, (standard gravity units, 'g')

65 fBodyBodyAccJerkMag-std(): Standard deviation of magnitude of Jerk signal of body acceleration in the frequency domain, (standard gravity units, 'g')

66 fBodyBodyGyroMag-mean():  Mean of magnitude of body angular velocity X2 in the frequency domain, (radians/second)

67 fBodyBodyGyroMag-std(): Standard deviation of magnitude of body angular velocity X2 in the frequency domain, (radians/second)

68 fBodyBodyGyroJerkMag-mean(): Mean of magnitude of Jerk signal of body angular velocity X2 in the frequency domain, (radians/second)

69 fBodyBodyGyroJerkMag-std(): Standard deviation of magnitude of Jerk signal of body angular velocity X2 in the frequency domain, (radians/second)
