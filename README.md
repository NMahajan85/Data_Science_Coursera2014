Data_Science_Coursera2014
=========================


##Work Performed on the original data set to get tidy data set
=================
*The data from "http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones"
was downloaded and the folder containing the data was set as the working directory for the project.

*The README.txt file provided much of the insight to the data contained in different files.

*The training data set X_train.txt and its labels (i.e. 1, 2, 3, 4, 5, 6) y_train.txt files were read into R from the train folder.

*Then subject_train.txt was read into R. It had information about the subject a number between 1 - 30 who volunteered for project. 

*Similarly, the test data set X_test.txt, its labels y_test.txt and subject_test.txt were read into R.

*Next, the features.txt file was read into R as a table. The second column contained names of all the variable (561 features). These names were assigned to train and test data set previously read into R.

*Using cbind subjects and labels were bound to test and train data set.

*Then to obtain a single data set test and train data sets were combined using rbind function. this data set had dimenssions 10299 X 563.

*grep function with arguments value = FALSE and fixed = TRUE was used to extract exact match for "-mean()" and "-std()" to obtain measurements on mean and standard deviation of each measurement. By using argument fixed = TRUE features like "meanFreq()" were not selected and hence not found in final data set.

*At tis point to add descriptive names of the activities to the data set, the activity_labels.txt file was read into R as table. Its columns were named as Activity and Activity_name. A new variable with name Activity_Name and as a factor was created in the data set based on last column of data set from previous step as it corresponded to the activity number. Then after forcing Activity_name into character, it was passed on to newly created factor variable Activity_Name in the data set to get data_final.

*To create tidy data set reshape package was loaded into the workspace. Using the melt function data frame data_final was melted and Subject, Activity and Activity_Name were used as id.vars. By omitting measure.vars value it was implied to treat all the remaining columns as variables. The data set was casted using cast function and passing Subject + Activity_Name ~ varaible as the formula and mean as fun. This gave a 180 X 68 dimensioned data set. 30 subjects, with each performing 6 activities. This data set provided the average of each variable 
for each activity and each subject.

*Finaly using write.table tidy_data.txt was created.
