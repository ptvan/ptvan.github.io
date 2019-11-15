---
layout: post
title: Time-series analysis of iPhone health data
---

I had exported biking distance, running distance and step counts from my iPhone in a
[previous post](https://ptvan.github.io/Python-MCMC-nuggets/). In that post, I tried to detected a supposed change in step count, using `pymc3` to model two different distributions. That was a valid, but rather simplistic approach. Since my step count has fairly good periodicity (and presumably is also a [stationary process](https://en.wikipedia.org/wiki/Stationary_process)), it's better to use time-series analysis. Relevant R code is found in my [timeseries_analysis.R](https://github.com/ptvan/R-snippets/blob/master/timeseries_analysis.R):

### The R time-series analysis ecosystem
The relevant data structures are base R's `ts` (time-series), `xts` (extended time-series) and `zoo`. The major packages are `lubridate` (mostly for cleaning and extracting times and dates), `zoo`, and `forecast`. For those interested in quantitative finance, there is `tidyquant`, which speaks xts and zoo in the Tidyverse syntax while interoperating with other domain-specific packages (`quantmod`, `PerformanceAnalytics`, etc..) 

### Handling times and dates
This is fairly straightforward: you can clean your data with `lubridate`, aggregate with `dplyr`, then convert it into one of the structures mentioned above. One thing to watch out for is missing data: many time-series functions expect an entry for every timepoint, so you may have to do some imputation.

### Exploratory analysis
This is where we test for stationarity by looking at [autocorrelation](https://en.wikipedia.org/wiki/Autocorrelation) and [partial autocorrelation](https://en.wikipedia.org/wiki/Partial_autocorrelation_function), look for spurious correlation with other variables in the dataset or external factors. 

### Decomposing data into seasonal, trend, and irregular components 
We can start with base R's `stl` function. If your data isn't seasonal (or seasonal enough), `stl` will fail with an informative message, which I think is better than trying to find an answer anyway.

### Modeling & prediction
Some techniques can get pretty sophisticated (eg. [Kalman filter](https://en.wikipedia.org/wiki/Kalman_filter))

### Reference

Since it's not exactly a new field, there are many, many books on time-series analysis. A recent one I find interesting is Aileen Nielsen's [Practical Time Series Analysis](https://www.oreilly.com/library/view/practical-time-series/9781492041641/). The writing is very accessible, there are plenty of references, and Nielsen alternated code examples between R and python. For some this could be a little disorienting, but I actually kind of liked it, since it showcases multiple tools.
