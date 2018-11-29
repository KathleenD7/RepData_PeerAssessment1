

```r
title: "Reproducible Research: Peer Assessment 1"
```

```
## Warning: NAs introduced by coercion
```

```
## Error in title:"Reproducible Research: Peer Assessment 1": NA/NaN argument
```

```r
output: 
  md_document
```

```
## Error in eval(expr, envir, enclos): object 'output' not found
```

```r
html_document:
    self_contained: no
```

```
## Error in eval(expr, envir, enclos): object 'self_contained' not found
```

```r
Read in the Data Set
```

```
## Error: <text>:1:6: unexpected 'in'
## 1: Read in
##          ^
```

```r
activity <- read.csv("~/Documents/Course5Week2/activity.csv")
```

What is the Total Number of Steps Taken Per Day?

```r
totalsteps<-sum(activity$steps,na.rm=TRUE)
print(totalsteps)
```

```
## [1] 570608
```

```r
sumdate<-aggregate(steps ~ date, activity, sum)
hist(sumdate$steps,main="Frequency of Total Number of Steps Per Day",xlab="Steps")
```

![plot of chunk unnamed-chunk-3](figure/unnamed-chunk-3-1.png)

```r
meansteps<-aggregate(steps ~ date, activity, mean)
print(meansteps)
```

```
##          date      steps
## 1  2012-10-02  0.4375000
## 2  2012-10-03 39.4166667
## 3  2012-10-04 42.0694444
## 4  2012-10-05 46.1597222
## 5  2012-10-06 53.5416667
## 6  2012-10-07 38.2465278
## 7  2012-10-09 44.4826389
## 8  2012-10-10 34.3750000
## 9  2012-10-11 35.7777778
## 10 2012-10-12 60.3541667
## 11 2012-10-13 43.1458333
## 12 2012-10-14 52.4236111
## 13 2012-10-15 35.2048611
## 14 2012-10-16 52.3750000
## 15 2012-10-17 46.7083333
## 16 2012-10-18 34.9166667
## 17 2012-10-19 41.0729167
## 18 2012-10-20 36.0937500
## 19 2012-10-21 30.6284722
## 20 2012-10-22 46.7361111
## 21 2012-10-23 30.9652778
## 22 2012-10-24 29.0104167
## 23 2012-10-25  8.6527778
## 24 2012-10-26 23.5347222
## 25 2012-10-27 35.1354167
## 26 2012-10-28 39.7847222
## 27 2012-10-29 17.4236111
## 28 2012-10-30 34.0937500
## 29 2012-10-31 53.5208333
## 30 2012-11-02 36.8055556
## 31 2012-11-03 36.7048611
## 32 2012-11-05 36.2465278
## 33 2012-11-06 28.9375000
## 34 2012-11-07 44.7326389
## 35 2012-11-08 11.1770833
## 36 2012-11-11 43.7777778
## 37 2012-11-12 37.3784722
## 38 2012-11-13 25.4722222
## 39 2012-11-15  0.1423611
## 40 2012-11-16 18.8923611
## 41 2012-11-17 49.7881944
## 42 2012-11-18 52.4652778
## 43 2012-11-19 30.6979167
## 44 2012-11-20 15.5277778
## 45 2012-11-21 44.3993056
## 46 2012-11-22 70.9270833
## 47 2012-11-23 73.5902778
## 48 2012-11-24 50.2708333
## 49 2012-11-25 41.0902778
## 50 2012-11-26 38.7569444
## 51 2012-11-27 47.3819444
## 52 2012-11-28 35.3576389
## 53 2012-11-29 24.4687500
```

```r
mediansteps<-aggregate(steps ~ date, activity, median)
print(mediansteps)
```

```
##          date steps
## 1  2012-10-02     0
## 2  2012-10-03     0
## 3  2012-10-04     0
## 4  2012-10-05     0
## 5  2012-10-06     0
## 6  2012-10-07     0
## 7  2012-10-09     0
## 8  2012-10-10     0
## 9  2012-10-11     0
## 10 2012-10-12     0
## 11 2012-10-13     0
## 12 2012-10-14     0
## 13 2012-10-15     0
## 14 2012-10-16     0
## 15 2012-10-17     0
## 16 2012-10-18     0
## 17 2012-10-19     0
## 18 2012-10-20     0
## 19 2012-10-21     0
## 20 2012-10-22     0
## 21 2012-10-23     0
## 22 2012-10-24     0
## 23 2012-10-25     0
## 24 2012-10-26     0
## 25 2012-10-27     0
## 26 2012-10-28     0
## 27 2012-10-29     0
## 28 2012-10-30     0
## 29 2012-10-31     0
## 30 2012-11-02     0
## 31 2012-11-03     0
## 32 2012-11-05     0
## 33 2012-11-06     0
## 34 2012-11-07     0
## 35 2012-11-08     0
## 36 2012-11-11     0
## 37 2012-11-12     0
## 38 2012-11-13     0
## 39 2012-11-15     0
## 40 2012-11-16     0
## 41 2012-11-17     0
## 42 2012-11-18     0
## 43 2012-11-19     0
## 44 2012-11-20     0
## 45 2012-11-21     0
## 46 2012-11-22     0
## 47 2012-11-23     0
## 48 2012-11-24     0
## 49 2012-11-25     0
## 50 2012-11-26     0
## 51 2012-11-27     0
## 52 2012-11-28     0
## 53 2012-11-29     0
```

What is the Average Daily Activity Pattern?

```r
AverageStepsPerInterval<-aggregate(steps ~ interval, activity, mean)
plot(AverageStepsPerInterval$interval,AverageStepsPerInterval$steps,type="l",main="Average Number of Steps Per Time Interval",xlab="Interval",ylab="Steps")
```

![plot of chunk unnamed-chunk-4](figure/unnamed-chunk-4-1.png)

```r
maxsteps<-max(AverageStepsPerInterval$steps)
maxinterval<-AverageStepsPerInterval$interval[AverageStepsPerInterval$steps==maxsteps]
print(maxinterval)
```

```
## [1] 835
```


Imputing Missing Values

```r
totalNAs<-sum(is.na(activity$steps))
print(totalNAs)
```

```
## [1] 2304
```

```r
##My strategy is to use the 5 minute interval means to fill in the NA values in the steps column of the activity table
meaninterval<-aggregate(steps ~ interval, activity, mean)
##I decided to use intervals instead of dates because there were missing dates when calculating the aggregate mean of dates
noNAsactivity<-activity
for(i in 1:nrow(noNAsactivity)){
  if (is.na(noNAsactivity[i,1])){
    noNAsactivity[i,1] <- meaninterval[which(noNAsactivity$interval[i]==meaninterval$interval),2]
  }
}
sumdate2<-aggregate(steps ~ date, noNAsactivity, sum)
hist(sumdate2$steps,main="Frequency of Total Number of Steps Per Day",xlab="Steps")
```

![plot of chunk unnamed-chunk-5](figure/unnamed-chunk-5-1.png)

```r
meansteps2<-aggregate(steps ~ date, noNAsactivity, mean)
print(meansteps2)
```

```
##          date      steps
## 1  2012-10-01 37.3825996
## 2  2012-10-02  0.4375000
## 3  2012-10-03 39.4166667
## 4  2012-10-04 42.0694444
## 5  2012-10-05 46.1597222
## 6  2012-10-06 53.5416667
## 7  2012-10-07 38.2465278
## 8  2012-10-08 37.3825996
## 9  2012-10-09 44.4826389
## 10 2012-10-10 34.3750000
## 11 2012-10-11 35.7777778
## 12 2012-10-12 60.3541667
## 13 2012-10-13 43.1458333
## 14 2012-10-14 52.4236111
## 15 2012-10-15 35.2048611
## 16 2012-10-16 52.3750000
## 17 2012-10-17 46.7083333
## 18 2012-10-18 34.9166667
## 19 2012-10-19 41.0729167
## 20 2012-10-20 36.0937500
## 21 2012-10-21 30.6284722
## 22 2012-10-22 46.7361111
## 23 2012-10-23 30.9652778
## 24 2012-10-24 29.0104167
## 25 2012-10-25  8.6527778
## 26 2012-10-26 23.5347222
## 27 2012-10-27 35.1354167
## 28 2012-10-28 39.7847222
## 29 2012-10-29 17.4236111
## 30 2012-10-30 34.0937500
## 31 2012-10-31 53.5208333
## 32 2012-11-01 37.3825996
## 33 2012-11-02 36.8055556
## 34 2012-11-03 36.7048611
## 35 2012-11-04 37.3825996
## 36 2012-11-05 36.2465278
## 37 2012-11-06 28.9375000
## 38 2012-11-07 44.7326389
## 39 2012-11-08 11.1770833
## 40 2012-11-09 37.3825996
## 41 2012-11-10 37.3825996
## 42 2012-11-11 43.7777778
## 43 2012-11-12 37.3784722
## 44 2012-11-13 25.4722222
## 45 2012-11-14 37.3825996
## 46 2012-11-15  0.1423611
## 47 2012-11-16 18.8923611
## 48 2012-11-17 49.7881944
## 49 2012-11-18 52.4652778
## 50 2012-11-19 30.6979167
## 51 2012-11-20 15.5277778
## 52 2012-11-21 44.3993056
## 53 2012-11-22 70.9270833
## 54 2012-11-23 73.5902778
## 55 2012-11-24 50.2708333
## 56 2012-11-25 41.0902778
## 57 2012-11-26 38.7569444
## 58 2012-11-27 47.3819444
## 59 2012-11-28 35.3576389
## 60 2012-11-29 24.4687500
## 61 2012-11-30 37.3825996
```

```r
mediansteps2<-aggregate(steps ~ date, noNAsactivity, median)
print(mediansteps2)
```

```
##          date    steps
## 1  2012-10-01 34.11321
## 2  2012-10-02  0.00000
## 3  2012-10-03  0.00000
## 4  2012-10-04  0.00000
## 5  2012-10-05  0.00000
## 6  2012-10-06  0.00000
## 7  2012-10-07  0.00000
## 8  2012-10-08 34.11321
## 9  2012-10-09  0.00000
## 10 2012-10-10  0.00000
## 11 2012-10-11  0.00000
## 12 2012-10-12  0.00000
## 13 2012-10-13  0.00000
## 14 2012-10-14  0.00000
## 15 2012-10-15  0.00000
## 16 2012-10-16  0.00000
## 17 2012-10-17  0.00000
## 18 2012-10-18  0.00000
## 19 2012-10-19  0.00000
## 20 2012-10-20  0.00000
## 21 2012-10-21  0.00000
## 22 2012-10-22  0.00000
## 23 2012-10-23  0.00000
## 24 2012-10-24  0.00000
## 25 2012-10-25  0.00000
## 26 2012-10-26  0.00000
## 27 2012-10-27  0.00000
## 28 2012-10-28  0.00000
## 29 2012-10-29  0.00000
## 30 2012-10-30  0.00000
## 31 2012-10-31  0.00000
## 32 2012-11-01 34.11321
## 33 2012-11-02  0.00000
## 34 2012-11-03  0.00000
## 35 2012-11-04 34.11321
## 36 2012-11-05  0.00000
## 37 2012-11-06  0.00000
## 38 2012-11-07  0.00000
## 39 2012-11-08  0.00000
## 40 2012-11-09 34.11321
## 41 2012-11-10 34.11321
## 42 2012-11-11  0.00000
## 43 2012-11-12  0.00000
## 44 2012-11-13  0.00000
## 45 2012-11-14 34.11321
## 46 2012-11-15  0.00000
## 47 2012-11-16  0.00000
## 48 2012-11-17  0.00000
## 49 2012-11-18  0.00000
## 50 2012-11-19  0.00000
## 51 2012-11-20  0.00000
## 52 2012-11-21  0.00000
## 53 2012-11-22  0.00000
## 54 2012-11-23  0.00000
## 55 2012-11-24  0.00000
## 56 2012-11-25  0.00000
## 57 2012-11-26  0.00000
## 58 2012-11-27  0.00000
## 59 2012-11-28  0.00000
## 60 2012-11-29  0.00000
## 61 2012-11-30 34.11321
```

```r
diffmeans<-mean(meansteps$steps)-mean(meansteps2$steps)
print(diffmeans)
```

```
## [1] 0
```

```r
diffmedians<-mean(mediansteps$steps)-mean(mediansteps2$steps)
print(diffmedians)
```

```
## [1] -4.473863
```

```r
##The new medians differ from the first part of the assignment
##The mean didn't change but the median for the new data is greater than the old data.
##Therefore, the impact of imputing missing data is that the values will change and the data can be skewed
```

Are there differences in Activity Patterns between Weekdays and Weekends?

```r
noNAsactivity$day<-weekdays(as.Date(noNAsactivity$date))

for(i in 1:nrow(noNAsactivity)){
  if (noNAsactivity$day[i]=="Sunday"){
    noNAsactivity$day[i] <- "Weekend"
  } 
}
for(i in 1:nrow(noNAsactivity)){
  if (noNAsactivity$day[i]=="Monday"){
    noNAsactivity$day[i] <- "Weekday"
  } 
}
for(i in 1:nrow(noNAsactivity)){
  if (noNAsactivity$day[i]=="Tuesday"){
    noNAsactivity$day[i] <- "Weekday"
  } 
}
for(i in 1:nrow(noNAsactivity)){
  if (noNAsactivity$day[i]=="Wednesday"){
    noNAsactivity$day[i] <- "Weekday"
  } 
}
for(i in 1:nrow(noNAsactivity)){
  if (noNAsactivity$day[i]=="Thursday"){
    noNAsactivity$day[i] <- "Weekday"
  } 
}
for(i in 1:nrow(noNAsactivity)){
  if (noNAsactivity$day[i]=="Friday"){
    noNAsactivity$day[i] <- "Weekday"
  } 
}
for(i in 1:nrow(noNAsactivity)){
  if (noNAsactivity$day[i]=="Saturday"){
    noNAsactivity$day[i] <- "Weekend"
  } 
}
noNAsactivity$day2<-weekdays(as.Date(noNAsactivity$date))
AverageStepsPerIntervalWE<-aggregate(steps ~ interval, subset(noNAsactivity,day=="Weekend"), mean)
AverageStepsPerIntervalWD<-aggregate(steps ~ interval, subset(noNAsactivity,day=="Weekday"), mean)
AverageStepsPerIntervalWD$Day<-"Weekday"
AverageStepsPerIntervalWE$Day<-"Weekend"
AverageStepsBoth<-rbind(AverageStepsPerIntervalWD,AverageStepsPerIntervalWE)
library(lattice)
xyplot(steps ~ interval | Day, data=AverageStepsBoth,layout=c(1,2),type="l",xlab="Interval",ylab="Steps")
```

![plot of chunk unnamed-chunk-6](figure/unnamed-chunk-6-1.png)
```

