##Week4-Project

## Step1: We download the zip file and unzip it in our workking directory.
Use read.table function to load the related dataframes.
Use rbind and cbind function to merge the datas.

## Examples:load
train.x <- read.table("UCI HAR Dataset/train/X_train.txt")
train.y <- read.table("UCI HAR Dataset/train/y_train.txt")

## Example:merge
fullData <- rbind(trainData, testData)
Here gives the rusult of our first step.

## Step2: The core step is to use the grep function to filter the feature names including mean and standrad deviation
as a list of index(featureindex) to help extract the data from the fullData we got in step1.
finalData is the result we expect.

## Step3: In this step we take the advantage of the feature of activityName
and then use factor function to substitute the factors.

## Example:re-factor
factor(finalData$activity, levels = activityName[,1], labels = activityName[,2])

## Step4: Just use function gsub.

## Example:rename
names(finalData) <- gsub("\\()", "", names(finalData))
[5] "tBodyAcc-mean()-Z"           "tBodyAcc-std()-X"            "tBodyAcc-std()-Y"            "tBodyAcc-std()-Z"      
to
[4] "timeBodyAccMean-Y"                "timeBodyAccMean-Z"                "timeBodyAccStd-X"   

## Step5: Use groupby and summarize to apply mean function to each subgroup.
We get groupdata as ourfinal result.
