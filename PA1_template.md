# Reproducible Research: Peer Assessment 1


## Loading and preprocessing the data
* Unzip the file to get the uncompressed activity.csv file.
* Then load this .csv file.


```r
unzip("activity.zip")
data<-read.csv("activity.csv")
```

## What is mean total number of steps taken per day?
* Do some basic data cleanup by replacing NA values in the step column with zeros prior to mean calculation. 
* Group the steps by date, calculate the total number of steps per day, plot a histogram of the total number
of steps/day, and report mean and median number of steps per day.


```r
library(dplyr)
data[is.na(data$steps), 1]<-c(0)
grouped <- group_by(data, date)
totalPerDay<-summarize(grouped, total=sum(steps))
meanPerDay<-mean(totalPerDay$total)
medianPerDay<-median(totalPerDay$total)
hist(totalPerDay$total, main="Histogram of Total Steps/Day", xlab="Total Steps/Day", ylim=c(0,30))
```

![](PA1_template_files/figure-html/unnamed-chunk-2-1.png) 
  
Create and output a table containing the mean and median steps per day.

```r
library(xtable)
tabData<-data.frame(Mean=meanPerDay, Median=medianPerDay)
xt<-xtable(tabData)
print(xt, include.rownames=FALSE, type="html")
```

<!-- html table generated in R 3.0.2 by xtable 1.7-4 package -->
<!-- Fri Sep 09 16:03:20 2016 -->
<table border=1>
<tr> <th> Mean </th> <th> Median </th>  </tr>
  <tr> <td align="right"> 9354.23 </td> <td align="right"> 10395.00 </td> </tr>
   </table>


## What is the average daily activity pattern?



## Imputing missing values



## Are there differences in activity patterns between weekdays and weekends?
