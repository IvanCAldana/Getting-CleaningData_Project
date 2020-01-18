# Getting-CleaningData_Project
Project for course Getting and Cleaning Data of Jhon Hopkins University

The script I wrote in Rstudio is below, and it intends to be self-explanatory by using comments troughout the code.

# Set Directory here
#setwd("D:/Documents/R/R-2016-2019/3. Getting and Cleaning Data/Homeworks/Week 4")
setwd("~/Documents/R/R-2016-2019/3. Getting and Cleaning Data/Homeworks/Week 4")

# You should create one R script called run_analysis.R that does the following:
# 1.Merges the training and the test sets to create one data set. 
# 2.Extracts only the measurements on the mean and standard deviation for each measurement.
# 3.Uses descriptive activity names to name the activities in the data set 
# 4.Appropriately labels the data set with descriptive variable names.
# 5.From the data set in step 4, creates a second independent tidy data set with the average of each variable
#   for each activity and each subject
#   Good luck!
#_________________________________________________________________________________________________________________________

# Reading a Local File
if (!file.exists("./data")){
  dir.create("./data")
}

fileUrl<-"https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip"
download.file(fileUrl,destfile="./data/Dataset.zip")
dateDownloaded<-date()
unzip("./data/Dataset.zip")

## Exploring the dataset.
# Read the data here using read.table. Identify the dimensions.
library(dplyr)

TestData_subject<-read.table("./UCI HAR Dataset/test/subject_test.txt",header = FALSE,col.names = "Subject")
TestData_ytest<-read.table("./UCI HAR Dataset/test/y_test.txt",header = FALSE,col.names = "Activity")
TestData_xtest<-read.table("./UCI HAR Dataset/test/X_test.txt",header = FALSE,as.is = TRUE)
TrainingData_subject<-read.table("./UCI HAR Dataset/train/subject_train.txt",header = FALSE,col.names = "Subject")
TrainingData_ytest<-read.table("./UCI HAR Dataset/train/y_train.txt",header = FALSE,col.names = "Activity")
TrainingData_xtest<-read.table("./UCI HAR Dataset/train/X_train.txt",header = FALSE,as.is = TRUE)
Activity_labels<-read.table("./UCI HAR Dataset/activity_labels.txt",header = FALSE,as.is = TRUE)
Features<-read.table("./UCI HAR Dataset/features.txt",header = FALSE,as.is = TRUE)

# Merging Data using base package commands cbind and rbind
TestData<-cbind(TestData_subject,TestData_ytest,TestData_xtest)
TrainingData<-cbind(TrainingData_subject,TrainingData_ytest,TrainingData_xtest)
MergedDataset<-rbind(TrainingData,TestData)

# Renaming columns of Datasets with descriptive variables names gotten directly from the files provided in Samsung data called here Features
Features_new<-c("Subject","Activity")
Features_new<-append(Features_new,Features[1:561,2])
colnames(MergedDataset)<-Features_new

# Extracting mean and standard deviation on each measurement using grep function, with codenames "mean()" and "std()"
Features1<-grep("Subject|Activity|mean()|std()",Features_new)
MergedData<-MergedDataset[,Features1]

# Name activities in the dataset by writing a For-Loop function, that extracts each label from file provided in Samsung Data called here as Activity_labels
Activity_names<-Rename_rows(MergedData,Activity_labels) # There must be a better way to do this!
Activity_names<-t(t(Activity_names))
FinalMergedData<-cbind(MergedData,Activity_names)

## Use the dplyr package to filter and sort our dataset just merged.
# Convert to tibble
tbl_df(FinalMergedData)

# select final columns for the tidyData
StatsData<-select(FinalMergedData,Subject,Activity_names,Activity,3:81,
                  -c(49:51,58:60,67:69,72,75,78,81))

# group by subjetc and activities and average mean and std data (columns)
Preliminary_TidyData <-
    StatsData %>%
    group_by(Subject,Activity_names) %>%
    summarize_all(funs(mean)) %>%
    print
    
# Arrange the dataset by subject and Activity in ascending order
TidyData<-arrange(Preliminary_TidyData,Subject,Activity)

# Write the Tidydata as .txt and .csv
write.table(TidyData,file="TidyData.txt",row.names = FALSE) #As text file
write.csv(TidyData,file="TidyData.csv") # As csv file

#_________________________________________________________________________________________________________________________
# Auxiliary function to create the row labels in line 58
Rename_rows <- function(MergedData,Activity_labels) 
{
    Rename_rows<-vector()
    for (i in 1:10299)
    {  
        #if (MergedData$Activity %in% Activity_labels$V1)
        #if (MergedData[i,2] %in% Activity_labels$V1)
        Activity_name<-Activity_labels[MergedData[i,2],2]
        Rename_rows<-append(Rename_rows,Activity_name)  
    }
    return(Rename_rows)
}
#_________________________________________________________________________________________________________________________
