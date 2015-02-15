# Reproducible Research: Peer Assessment 1


## Loading and preprocessing the data

```r
library(ggplot2)
Sys.setlocale("LC_TIME", "English")
```

```
## [1] "English_United States.1252"
```

```r
data<-read.csv(unz("activity.zip", "activity.csv"))
data <- transform(data, date = as.POSIXct(date))
```
## What is mean total number of steps taken per day?

```r
sumpd<-tapply(data$steps, data$date, sum)
sumpd <- data.frame(date=names(sumpd),steps = sumpd,row.names=NULL)
sumpd  <- transform(sumpd , date = as.POSIXct(date))
par(mar = c(5, 4, 1, 1),las =1)
qplot(date,steps,data = sumpd,geom = "histogram",stat="identity")
```

```
## Warning: Removed 8 rows containing missing values (position_stack).
```

![](PA1_template_files/figure-html/histogram-1.png) 

```r
mean(sumpd$steps,na.rm= TRUE)
```

```
## [1] 10766.19
```

```r
median(sumpd$steps, na.rm = TRUE)
```

```
## [1] 10765
```


## What is the average daily activity pattern?



## Imputing missing values



## Are there differences in activity patterns between weekdays and weekends?
