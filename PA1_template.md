---
title: "Reproducible Research Project 1 - Activity Analysis"
date: "Saturday, August 16, 2014"
output: html_document
---

##Loading and preprocessing the data


```r
activityData = read.csv("activity.csv",colClasses=c("integer","Date","integer"))
library(plyr)
activitySum <- ddply(activityData, .(date),colwise(sum))
plot(activitySum$date,activitySum$steps,type="h",xlab="Date",ylab="Total # of Steps",main="Total Steps Taken Per Day Histogram")
```

![plot of chunk unnamed-chunk-1](figure/unnamed-chunk-1.png) 

##Mean total number of steps taken per day


```r
activityDailyMean <- ddply(activityData, .(date),colwise(mean),na.rm=T)

activityDailyMean
```

```
##          date   steps interval
## 1  2012-10-01     NaN     1178
## 2  2012-10-02  0.4375     1178
## 3  2012-10-03 39.4167     1178
## 4  2012-10-04 42.0694     1178
## 5  2012-10-05 46.1597     1178
## 6  2012-10-06 53.5417     1178
## 7  2012-10-07 38.2465     1178
## 8  2012-10-08     NaN     1178
## 9  2012-10-09 44.4826     1178
## 10 2012-10-10 34.3750     1178
## 11 2012-10-11 35.7778     1178
## 12 2012-10-12 60.3542     1178
## 13 2012-10-13 43.1458     1178
## 14 2012-10-14 52.4236     1178
## 15 2012-10-15 35.2049     1178
## 16 2012-10-16 52.3750     1178
## 17 2012-10-17 46.7083     1178
## 18 2012-10-18 34.9167     1178
## 19 2012-10-19 41.0729     1178
## 20 2012-10-20 36.0938     1178
## 21 2012-10-21 30.6285     1178
## 22 2012-10-22 46.7361     1178
## 23 2012-10-23 30.9653     1178
## 24 2012-10-24 29.0104     1178
## 25 2012-10-25  8.6528     1178
## 26 2012-10-26 23.5347     1178
## 27 2012-10-27 35.1354     1178
## 28 2012-10-28 39.7847     1178
## 29 2012-10-29 17.4236     1178
## 30 2012-10-30 34.0938     1178
## 31 2012-10-31 53.5208     1178
## 32 2012-11-01     NaN     1178
## 33 2012-11-02 36.8056     1178
## 34 2012-11-03 36.7049     1178
## 35 2012-11-04     NaN     1178
## 36 2012-11-05 36.2465     1178
## 37 2012-11-06 28.9375     1178
## 38 2012-11-07 44.7326     1178
## 39 2012-11-08 11.1771     1178
## 40 2012-11-09     NaN     1178
## 41 2012-11-10     NaN     1178
## 42 2012-11-11 43.7778     1178
## 43 2012-11-12 37.3785     1178
## 44 2012-11-13 25.4722     1178
## 45 2012-11-14     NaN     1178
## 46 2012-11-15  0.1424     1178
## 47 2012-11-16 18.8924     1178
## 48 2012-11-17 49.7882     1178
## 49 2012-11-18 52.4653     1178
## 50 2012-11-19 30.6979     1178
## 51 2012-11-20 15.5278     1178
## 52 2012-11-21 44.3993     1178
## 53 2012-11-22 70.9271     1178
## 54 2012-11-23 73.5903     1178
## 55 2012-11-24 50.2708     1178
## 56 2012-11-25 41.0903     1178
## 57 2012-11-26 38.7569     1178
## 58 2012-11-27 47.3819     1178
## 59 2012-11-28 35.3576     1178
## 60 2012-11-29 24.4688     1178
## 61 2012-11-30     NaN     1178
```


##Median total number of steps taken per day


```r
activityDailyMedian <- ddply(activityData, .(date),colwise(median),na.rm=T)

activityDailyMedian
```

```
##          date steps interval
## 1  2012-10-01    NA     1178
## 2  2012-10-02     0     1178
## 3  2012-10-03     0     1178
## 4  2012-10-04     0     1178
## 5  2012-10-05     0     1178
## 6  2012-10-06     0     1178
## 7  2012-10-07     0     1178
## 8  2012-10-08    NA     1178
## 9  2012-10-09     0     1178
## 10 2012-10-10     0     1178
## 11 2012-10-11     0     1178
## 12 2012-10-12     0     1178
## 13 2012-10-13     0     1178
## 14 2012-10-14     0     1178
## 15 2012-10-15     0     1178
## 16 2012-10-16     0     1178
## 17 2012-10-17     0     1178
## 18 2012-10-18     0     1178
## 19 2012-10-19     0     1178
## 20 2012-10-20     0     1178
## 21 2012-10-21     0     1178
## 22 2012-10-22     0     1178
## 23 2012-10-23     0     1178
## 24 2012-10-24     0     1178
## 25 2012-10-25     0     1178
## 26 2012-10-26     0     1178
## 27 2012-10-27     0     1178
## 28 2012-10-28     0     1178
## 29 2012-10-29     0     1178
## 30 2012-10-30     0     1178
## 31 2012-10-31     0     1178
## 32 2012-11-01    NA     1178
## 33 2012-11-02     0     1178
## 34 2012-11-03     0     1178
## 35 2012-11-04    NA     1178
## 36 2012-11-05     0     1178
## 37 2012-11-06     0     1178
## 38 2012-11-07     0     1178
## 39 2012-11-08     0     1178
## 40 2012-11-09    NA     1178
## 41 2012-11-10    NA     1178
## 42 2012-11-11     0     1178
## 43 2012-11-12     0     1178
## 44 2012-11-13     0     1178
## 45 2012-11-14    NA     1178
## 46 2012-11-15     0     1178
## 47 2012-11-16     0     1178
## 48 2012-11-17     0     1178
## 49 2012-11-18     0     1178
## 50 2012-11-19     0     1178
## 51 2012-11-20     0     1178
## 52 2012-11-21     0     1178
## 53 2012-11-22     0     1178
## 54 2012-11-23     0     1178
## 55 2012-11-24     0     1178
## 56 2012-11-25     0     1178
## 57 2012-11-26     0     1178
## 58 2012-11-27     0     1178
## 59 2012-11-28     0     1178
## 60 2012-11-29     0     1178
## 61 2012-11-30    NA     1178
```



##What is the average daily activity pattern?

```r
acticiyTimeoftheDayMean <- ddply(activityData, .(interval),colwise(mean),na.rm=T)

acticiyTimeoftheDayMean$interval <- as.POSIXlt(strptime(paste(acticiyTimeoftheDayMean$date,sprintf("%04i",acticiyTimeoftheDayMean$interval),length=4),"%Y-%m-%d%H%M"),tz = "GMT")

plot(acticiyTimeoftheDayMean$interval,acticiyTimeoftheDayMean$steps,t="l",,main="Daily Time of the Day Activity Graph", xlab="Time of the Day", ylab = "Average Steps")
```

![plot of chunk unnamed-chunk-4](figure/unnamed-chunk-4.png) 

```r
subset(acticiyTimeoftheDayMean,steps == max(acticiyTimeoftheDayMean$steps),select = interval)
```

```
##                interval
## 104 2012-10-31 08:35:00
```

# The Maximum number of steps are are at interval 8:35 AM


#The number of NA data points are shown below


```r
count(activityData[is.na(activityData)])
```

```
##      x freq
## 1 <NA> 2304
```

##Imputing missing values


```r
count(activityData[is.na(activityData)])
```

```
##      x freq
## 1 <NA> 2304
```

```r
#Fill NAs with mean of steps for that timeoftheday

acticiyTimeoftheDayMeanForFill <- ddply(activityData, .(interval),colwise(mean),na.rm=T)

missVals <- is.na(activityData$steps)

activityDataFill <- activityData

for (i in 1:nrow(activityData))
{
  if (missVals[i])
  {
    activityDataFill[i,1] <- subset(acticiyTimeoftheDayMeanForFill,interval == activityData[i,3])$steps
  }
}
```

## Mean and median is same, before and after imputing, as imputing is based on mean from non.NA observations


```r
is.weekday <- function(x = NULL)
{
  if (is.null(x))
    return(NULL)
  
  retVec <- vector(mode = "logical",length = length(x))
  for (i in 1:length(x))
  {
    if (weekdays(x[i]) == "Saturday" | weekdays(x[i]) == "Sunday" )
    {
      retVec[i] <- FALSE
    }
    else
    {
      retVec[i] <- TRUE
    }
  }
  return(retVec)
}

weekdayVec <- is.weekday(activityDataFill$date)

activityDataFillWeekday <- activityDataFill[weekdayVec,]

activityDataFillWeekend <- activityDataFill[!weekdayVec,]


weekdayTimeoftheDayMean <- ddply(activityDataFillWeekday, .(interval),colwise(mean),na.rm=T)

weekdayTimeoftheDayMean$interval <- as.POSIXlt(strptime(paste(weekdayTimeoftheDayMean$date,sprintf("%04i",weekdayTimeoftheDayMean$interval),length=4),"%Y-%m-%d%H%M"),tz = "GMT")



weekendTimeoftheDayMean <- ddply(activityDataFillWeekend, .(interval),colwise(mean),na.rm=T)

weekendTimeoftheDayMean$interval <- as.POSIXlt(strptime(paste(weekendTimeoftheDayMean$date,sprintf("%04i",weekendTimeoftheDayMean$interval),length=4),"%Y-%m-%d%H%M"),tz = "GMT")



par(mfrow=c(2,1))

plot(weekdayTimeoftheDayMean$interval,weekdayTimeoftheDayMean$steps,t="l",main="Weekday Activity Graph", xlab="Time of the Day", ylab = "Average Steps",col="blue")

plot(weekendTimeoftheDayMean$interval,weekendTimeoftheDayMean$steps,t="l",main="Weekend Activity Graph", xlab="Time of the Day", ylab = "Average Steps",col="blue")
```

![plot of chunk unnamed-chunk-7](figure/unnamed-chunk-7.png) 






