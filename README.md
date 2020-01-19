# GETTING AND CLEANING DATA PROJECT
- Project for course Getting and Cleaning Data of Jhon Hopkins University

- The script I wrote in Rstudio is attached in this repo as Run_analysis.R, and it intends to be self-explanatory by using comments troughout the code.

- The basic guidelines are given as follows:

You should create one R script called run_analysis.R that does the following:

1.Merges the training and the test sets to create one data set. 

2.Extracts only the measurements on the mean and standard deviation for each measurement.

3.Uses descriptive activity names to name the activities in the data set 

4.Appropriately labels the data set with descriptive variable names.

5.From the data set in step 4, creates a second independent tidy data set with the average of each variable for each activity and each subject

Good luck!

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
 
 
- The variables extracted and the units are all defined in the Codebook.md of this repo.
