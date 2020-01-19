## A bried description of the process used

# About the data

- The data obtained from Samsung Data was found in the following order:

- On the UCI HAR Folder:

On the train folder:

1. subject_train.txt: One file containing the numeric tag for the subject performing the excercises (1,2,3,4...up to 30)
2. X_train.txt: One file containing the numeric tag for the activity being performed (1,2,3,4,5,6)
3. Y_train.txt: One file containing the raw data of each variable measured/computed during the experiment.

On the test folder:

4. subject_test.txt: One file containing the numeric tag for the subject performing the excercises (1,2,3,4...up to 30)
5. X_test.txt: One file containing the numeric tag for the activity being performed (1,2,3,4,5,6)
6. Y_test.txt: One file containing the raw data of each variable measured/Computed during the experiment.

Additionally on the UCI HAR folder data on activity names (activity_labels.txt) and features (features.txt) were imported. 

# Reading the data

- Therefore, the eight files or dataset read into R, were named as:

1. TestData_subject (integer of 2947 obs)
2. TestData_ytest (integer of 2947 obs)
3. TestData_xtest (numeric values of 2947 obs and 561 variables)
4. TrainingData_subject (integer of 7352 obs)
5. TrainingData_ytest (integer of 7352 obs)
6. TrainingData_xtest (numeric values of 7352 obs and 561 variables)
7. Activity_labels ( 6 obs of 1 variable (character values like "STANDING","WALKING",etc...))
8. Features (561 obs of 1 variable (character values like "tBodyAcc-mean()-X","tBodyAcc-mean()-Y", and so on))

# Merging DataSet

- Data imported was merged as follows:

Test data was merged using cbind() operator (TestData variable in R) 
Training data was merged using cbind() operator (TrainingData variable in R)
Preliminary merged dataset was merged (from test and training data) using rbind() operator (MergedDataset variable in R)

# Naming columns (variables) names

- A vector of variables names was prepared from the Features variable (or Features.txt file) using colnames() function and assigned to
the preliminary merged dataser (MergedDataset)

# Extracting mean and standard deviation from each measurement

- A smaller dataset was extracted from MergedDataset






The TidyDataset included here contains the following information extracted from the Samsung Data files

1  Subject: Tag of each individual who performed the excercises

2  Activity_names: Names of the activities performed by each individual

3  Activity: Tag for each activity performed by each individual

4  tBodyAcc-mean()-X: Mean of body accelaration in the X direction in the time domain

5  tBodyAcc-mean()-Y: Mean of body accelaration in the Y direction in the time domain

6  tBodyAcc-mean()-Z: Mean of body accelaration in the Z direction in the time domain

7  tBodyAcc-std()-X: Standard deviation of body accelaration in the X direction in the time domain

8  tBodyAcc-std()-Y: Standard deviation of body accelaration in the Y direction in the time domain

9  tBodyAcc-std()-Z: Standard deviation of body accelaration in the Z direction in the time domain

10 tGravityAcc-mean()-X: Mean of gravity acceleration in the X direction in the time domain

11 tGravityAcc-mean()-Y: Mean of gravity acceleration in the Y direction in the time domain

12 tGravityAcc-mean()-Z: Mean of gravity acceleration in the Z direction in the time domain

13 tGravityAcc-std()-X: Standard deviation of gravity acceleration in the X direction in the time domain

14 tGravityAcc-std()-Y: Standard deviation of gravity acceleration in the Y direction in the time domain

15 tGravityAcc-std()-Z: Standard deviation of gravity acceleration in the Z direction in the time domain

16 tBodyAccJerk-mean()-X: Mean of Jerk signal of body acceleration in the X direction in the time domain

17 tBodyAccJerk-mean()-Y: Mean of Jerk signal of body acceleration in the Y direction in the time domain

18 tBodyAccJerk-mean()-Z: Mean of Jerk signal of body acceleration in the Z direction in the time domain

19 tBodyAccJerk-std()-X: Standard deviation of Jerk signal of body acceleration in the X direction in the time domain

20 tBodyAccJerk-std()-Y: Standard deviation of Jerk signal of body acceleration in the Y direction in the time domain

21 tBodyAccJerk-std()-Z: Standard deviation of Jerk signal of body acceleration in the Z direction in the time domain

22 tBodyGyro-mean()-X: Mean of body angular velocity in the X direction in the time domain

23 tBodyGyro-mean()-Y: Mean of body angular velocity in the Y direction in the time domain

24 tBodyGyro-mean()-Z: Mean of body angular velocity in the Z direction in the time domain

25 tBodyGyro-std()-X: Standard deviation of body angular velocity in the X direction in the time domain

26 tBodyGyro-std()-Y: Standard deviation of body angular velocity in the Y direction in the time domain

27 tBodyGyro-std()-Z: Standard deviation of body angular velocity in the Z direction in the time domain

28 tBodyGyroJerk-mean()-X: Mean of Jerk signal of body angular velocity in the X direction in the time domain

29 tBodyGyroJerk-mean()-Y: Mean of Jerk signal of body angular velocity in the Y direction in the time domain

30 tBodyGyroJerk-mean()-Z: Mean of Jerk signal of body angular velocity in the Z direction in the time domain

31 tBodyGyroJerk-std()-X: Standard deviation of Jerk signal of body angular velocity in the X direction in the time domain

32 tBodyGyroJerk-std()-Y: Standard deviation of Jerk signal of body angular velocity in the Y direction in the time domain

33 tBodyGyroJerk-std()-Z: Standard deviation of Jerk signal of body angular velocity in the Z direction in the time domain

34 tBodyAccMag-mean(): Mean of magnitude of body acceleration in the time domain

35 tBodyAccMag-std(): Standard deviation of magnitude of body acceleration in the time domain

36 tGravityAccMag-mean(): Mean of magnitude of gravity acceleration in the time domain

37 tGravityAccMag-std(): Standard deviation of magnitude of gravity acceleration in the time domain

38 tBodyAccJerkMag-mean(): Mean of magnitude of Jerk signal of body acceleration in the time domain

39 tBodyAccJerkMag-std(): Standard deviation of magnitude of Jerk signal of body acceleration in the time domain

40 tBodyGyroMag-mean(): Mean of magnitude of body angular velocity in the time domain

41 tBodyGyroMag-std(): Standard deviation of magnitude of body angular velocity in the time domain

42 tBodyGyroJerkMag-mean(): Mean of magnitude of Jerk signal of body angular velocity in the time domain

43 tBodyGyroJerkMag-std(): Standard deviation of magnitude of Jerk signal of body angular velocity in the time domain

44 fBodyAcc-mean()-X: Mean of body acceleration in the X direction in the frequency domain

45 fBodyAcc-mean()-Y: Mean of body acceleration in the Y direction in the frequency domain

46 fBodyAcc-mean()-Z: Mean of body acceleration in the Z direction in the frequency domain

47 fBodyAcc-std()-X: Standard deviation of body acceleration in the X direction in the frequency domain

48 fBodyAcc-std()-Y: Standard deviation of body acceleration in the Y direction in the frequency domain

49 fBodyAcc-std()-Z: Standard deviation of body acceleration in the Z direction in the frequency domain

50 fBodyAccJerk-mean()-X: Mean of Jerk signal of body acceleration in the X direction in the frequency domain

51 fBodyAccJerk-mean()-Y: Mean of Jerk signal of body acceleration in the Y direction in the frequency domain

52 fBodyAccJerk-mean()-Z: Mean of Jerk signal of body acceleration in the Z direction in the frequency domain

53 fBodyAccJerk-std()-X: Standard deviation of Jerk signal of body acceleration in the X direction in the frequency domain

54 fBodyAccJerk-std()-Y: Standard deviation of Jerk signal of body acceleration in the Y direction in the frequency domain

55 fBodyAccJerk-std()-Z: Standard deviation of Jerk signal of body acceleration in the Z direction in the frequency domain

56 fBodyGyro-mean()-X: Mean of body angular velocity in the X direction in the frequency domain

57 fBodyGyro-mean()-Y: Mean of body angular velocity in the Y direction in the frequency domain

58 fBodyGyro-mean()-Z: Mean of body angular velocity in the Z direction in the frequency domain

59 fBodyGyro-std()-X: Standard deviation of body angular velocity in the X direction in the frequency domain

60 fBodyGyro-std()-Y: Standard deviation of body angular velocity in the Y direction in the frequency domain

61 fBodyGyro-std()-Z: Standard deviation of body angular velocity in the Z direction in the frequency domain

62 fBodyAccMag-mean(): Mean of magnitude of body acceleration in the frequency domain

63 fBodyAccMag-std(): Standard deviation of magnitude of body acceleration in the frequency domain

64 fBodyBodyAccJerkMag-mean(): Mean of magnitude of Jerk signal of body acceleration in the frequency domain

65 fBodyBodyAccJerkMag-std(): Standard deviation of magnitude of Jerk signal of body acceleration in the frequency domain

66 fBodyBodyGyroMag-mean():  Mean of magnitude of body angular velocity X2 in the frequency domain

67 fBodyBodyGyroMag-std(): Standard deviation of magnitude of body angular velocity X2 in the frequency domain

68 fBodyBodyGyroJerkMag-mean(): Mean of magnitude of Jerk signal of body angular velocity X2 in the frequency domain

69 fBodyBodyGyroJerkMag-std(): Standard deviation of magnitude of Jerk signal of body angular velocity X2 in the frequency domain
