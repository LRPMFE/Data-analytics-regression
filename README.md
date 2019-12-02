---
title: "UBS TakeHomeAssigment"
author: "Rongpeng Liu"
date: "October 31, 2019"
output: pdf_document
---
```{r global_options, include=FALSE}
knitr::opts_chunk$set(fig.width=12, fig.height=8, fig.path='Figs/', warning=FALSE, message=FALSE)
```

## Question 1: Outlier detection and statistics

(a) Load the data of the csv file into a data format of your choice.

```{r include=FALSE}
setwd("C:/Users/52994/Desktop/UBS test")
```

```{r warning=FALSE}
library(data.table)

# Load data, change column names, set as data.table and change data type
DT <- as.data.table(read.csv("data.csv", header = F))
DT <- t(DT)
colnames(DT) <- c("date", "Equity1", "Equity2", "VIX", "libor_1M")
DT <- as.data.table(DT[-1,])
DT[] <- lapply(DT, function(x) as.numeric(x))
DT$day=as.character("01")
DT$date <- as.Date(with(DT, paste(date, day)), "%Y%m%d")
DT <- DT[,-6]

head(DT, 5)
```

After loading data, the first 5 rows are shown above.
