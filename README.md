# GettingAndCleaningDataAssignment

## Note: 
Data files must be stores in your working directory. They can be stored directly (all in the same folder) or you can have the files "features.txt", "activity_labels.txt" in your working directory, and the test and train files, in its folder ("/test" and "/train") as you get when you decompress the zip file with the data.

## Packages you'll need:
You must have installed the "dplyr" package. 

## Code
We start loading the files (the common files first: labels, features:
 
    lab <- read.csv("activity_labels.txt",sep="", header = F)
    fea <- read.csv2("features.txt",sep="", header = F, stringsAsFactors = F)
    
Now, we load the test files (subject, X, and Y files):

    if (file.exists("X_test.txt")){
         x_test <- read.table("X_test.txt",sep="",header = F)
    } else if (file.exists("./test/X_test.txt")){
         x_test <- read.table("./test/X_test.txt",sep="",header = F)     
    } else {
         print("ERROR: I cann't find the file X_test.txt")
    }
    
    if (file.exists("Y_test.txt")){
         y_test <- read.csv2("Y_test.txt",sep="",header = F)     
    } else if (file.exists("./test/Y_test.txt")) {
         y_test <- read.csv2("./test/Y_test.txt",sep="",header = F)     
    } else {
         print("ERROR: I cann't find the file Y_test.txt")
    }
    
    if (file.exists("subject_test.txt")){
         subject_test <- read.csv("subject_test.txt", sep="", header = F)
    } else if (file.exists("./test/subject_test.txt")){
         subject_test <- read.csv("./test/subject_test.txt", sep="", header = F)     
    } else {
         print("ERROR: I cann't find the file subject_test.txt")
    }
 
Before to load the train files, we combine the files and get a new dataset. We load the 'dplyr' package. Remember you must have this installed first!

    library(dplyr)
    XT <- tbl_df(x_test)
    FE <- tbl_df(fea)
    names(y_test) <- c("num_act")
    names(lab) <- c("num_act","activity")
    y_test <- left_join(y_test,lab, by="num_act")
    YT <- tbl_df(y_test)
    
There are some duplicate names in the features data, so we add a new column that combine the feature name with the row number:

    FE <- FE %>% mutate(goodnames = paste(V1, V2, sep=" "))

We add the names (features file) to XT. It's easier now.

    nm <- FE$goodnames
    names(XT) <- nm

Now, we can select the columns we need (mean and std):

    XT2 <- XT %>% select(contains("mean()"), contains("std"))

We change the name col to subject_test:

    names(subject_test)<-c("subject")
    ST <- tbl_df(subject_test)

We add an id column in each tables

    ST <- ST %>% mutate(id=1:2947)
    XT2 <- XT2 %>% mutate(id=1:2947)
    YT <- YT %>% mutate(id=1:2947)
    
And now, we use join to get a new dataset:

    DTS <- full_join(ST, YT, by = "id")
    DTS <- full_join(DTS, XT2, by = "id")

In this moment, we have DTS which has the information we need, but only about the test data, we are going to use the same approach with the train data. We'll get a new object: DTR, and then we'll merge both to get the global dataset: DTT.

    if (file.exists("X_train.txt")){
         x_train <- read.table("X_train.txt",sep="",header = F)
    } else if (file.exists("./train/X_train.txt")){
         x_train <- read.table("./train/X_train.txt",sep="",header = F)
    } else {
         print("ERROR: I cann't find the file X_train.txt")
    }
    if (file.exists("Y_train.txt")){
         y_train <- read.csv2("Y_train.txt",sep="",header = F)
    } else if (file.exists("./train/Y_train.txt")){
         y_train <- read.csv2("./train/Y_train.txt",sep="",header = F)     
    } else {
         print("ERROR: I cann't find the file Y_train.txt")
    }
    if (file.exists("subject_train.txt")) {
         subject_train <- read.csv("subject_train.txt", sep="", header = F)
    } else if(file.exists("./train/subject_train.txt")) {
         subject_train <- read.csv("./train/subject_train.txt", sep="", header = F)
    } else {
         print("ERROR: I cann't find the file subject_train.txt")
    }

    XR <- tbl_df(x_train)
    names(y_train) <- c("num_act")
    y_train <- left_join(y_train,lab, by="num_act")
    YR <- tbl_df(y_train)
    
We use the vector (nm) with the correct features names to rename the XR's columns:

    names(XR) <- nm

We select the columns we need:

    XR2 <- XR %>% select(contains("mean()"), contains("std"))

We change the name col to subject_train:

    names(subject_train)<-c("subject")
    SR <- tbl_df(subject_train)

We add an id column

    SR <- SR %>% mutate(id=1:7352)
    XR2 <- XR2 %>% mutate(id=1:7352)
    YR <- YR %>% mutate(id=1:7352)

And now, we use join to get a new dataset (DTR):

    DTR <- full_join(SR, YR, by = "id")
    DTR <- full_join(DTR, XR2, by = "id")
    
Previous to merge the two dataframes, DTS and DTR we are going to erase the column id in both (it has no sense keep them by now, because every one starts on 1 to... Anyway we can add another one id later, (for 1 to n) if we need

    DTS <- DTS %>% transmute(id=NULL)
    DTR <- DTR %>% transmute(id=NULL)
    
Now, we merge the dataframes

    DTT <- bind_rows(DTR,DTS)
    
As the assignment ask 'use descriptive activity names to name the activities in the data set' I drop the "num_act" column

    DTT <- DTT %>% transmute(num_act=NULL)
    
Now, we are goint to get a new dataset, with the mean of the values for every subject and activity:

    DTM <- DTT %>% group_by(subject,activity) %>% summarise_each(funs(mean))

And, we write the dataframe in a file (its name will be 'DataSet5.txt' and you can find it in your working directory)

    write.table(DTM, file="DataSet5.txt",row.names = FALSE)


## About the names of variables and activities
I haven't changed the activity names because I think they are pretty descriptive and, in my opinion, there isn't any reason to change them. On the other hand, the variable names has been changed combining the number or row and the original name. There was columns (in features.txt) with the same name, and, in order to fix it, I add a new column containing the row number + old name. I was thinking about take the number out later, but, really I believe that it doesn't concern to the assignment requirements, so I leave them. If you think they must be without the number, please, excuse me.





    
