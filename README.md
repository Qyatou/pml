# pml
Prediction Assignment Writeup

Load Data
> train<- read.csv("E://pml-training.csv",na.strings=c("NA","","#DIV/0!"))
> dim(train)
[1] 19622   160     
> test<- read.csv("E://pml-testing.csv",na.strings=c("NA","","#DIV/0!"))
> dim(test)
[1]  20 160

Tidy the Data

counts <- colSums(is.na(train))
> table(counts)
counts
    0 19216 19217 19218 19220 19221 19225 19226 19227 19248 19293 19294 
   60    67     1     1     1     4     1     4     2     2     1     1 
19296 19299 19300 19301 19622 
    2     1     4     2     6 
>training <- train[counts == 0]
> dim(training)
[1] 19622    60
> trainset<- training[c(-1, -3, -4, -5, -6)]
> dim(trainset)
[1] 19622    55

> countstest <- colSums(is.na(test))
> table(countstest)
countstest
  0  20 
 60 100 
> testing<- test[countstest == 0]
> dim(testing)
[1] 20 60
> testset<- testing[c(-1, -3, -4, -5, -6)]
> dim(testset)
[1] 20 55

Explore and Preprocess Data

> table(train$user_name)

  adelmo carlitos  charles   eurico   jeremy    pedro 
    3892     3112     3536     3070     3402     2610 

