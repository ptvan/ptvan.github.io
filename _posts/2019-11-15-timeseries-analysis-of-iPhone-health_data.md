---
layout: post
title: Time-series analysis of iPhone health data
---

I had exported biking distance, running distance and step counts from my iPhone in a
[previous post](https://ptvan.github.io/Python-MCMC-nuggets/). In that post, I tried to detected a possible change in daily step count, using `pymc3` to model two different distributions. While this achieves the goal of detecting a single changepoint, there is a lot more we can do with this time series. For example, my biking is presumably a [stationary process](https://en.wikipedia.org/wiki/Stationary_process) and possibly could have _some_ periodicity, we can try to model these using time-series tools. Relevant R code is found in my [timeseries_analysis.R](https://github.com/ptvan/R-snippets/blob/master/timeseries_analysis.R).

### The R time-series analysis ecosystem
The relevant data structures are base R's `ts` (time-series), `xts` (extended time-series) and `zoo`. The major packages are `lubridate` (mostly for cleaning and extracting times and dates), `zoo`, and `forecast`. For those interested in quantitative finance, there is `tidyquant`, which speaks xts and zoo in the Tidyverse syntax while interoperating with other domain-specific packages (`quantmod`, `PerformanceAnalytics`, etc..) 

### Handling times and dates
This is fairly straightforward: you can clean your data with `lubridate`, aggregate with `dplyr`, then convert it into one of the structures mentioned above. One thing to watch out for is missing data: many time-series functions expect an entry for every timepoint, so you may have to do some imputation.

### Exploratory analysis
This is where we test for stationarity by looking at [autocorrelation](https://en.wikipedia.org/wiki/Autocorrelation) and [partial autocorrelation](https://en.wikipedia.org/wiki/Partial_autocorrelation_function), look for spurious correlation with other variables in the dataset or external factors. You may also need to perform smoothing using [Kalman filter](https://en.wikipedia.org/wiki/Kalman_filter).

### Decomposing data into seasonal, trend, and irregular components 
We can start with base R's `stl` (Seasonal Decomposition of Time Series by Loess). If your data isn't seasonal (or seasonal enough), `stl()` will fail with an informative message, which I think is better than trying to find an answer anyway. After removing seasonal and trend components, we can start looking at detecting anomalies. STL can also perform forecasting (see below).

### Detecting anomalies
Timeseries anomalies are generally divided into *outliers*, which are local temporary data points, and *changepoints*, which represents a shift to a fundamentally state in the data.

You can use `stl()` itself to detect outliers, since as I mentioned above, that is what remains in the data once seasonal and trend components have been removed. However, when decomposing data where the trend component is less dominant than the seasonal component, the loess smoother tends to perform worse, as described by the authors of the `anomalize` package [here](https://cran.r-project.org/web/packages/anomalize/vignettes/anomalize_methods.html). You can simply use [IQR](https://en.wikipedia.org/wiki/Interquartile_range) to flag outliers. Twitter, who has access to tons of seasonal data, created the [AnomalyDetection](https://blog.twitter.com/engineering/en_us/a/2015/introducing-practical-and-robust-anomaly-detection-in-a-time-series.html) package, which uses a refined version of the [Generalized ESD test](https://www.itl.nist.gov/div898/handbook/eda/section3/eda35h3.htm). 

For detecting changepoints, I used the `changepoint` package, which implements different algorithms, including [Binary Segmentation](https://www.jstor.org/stable/2529204), At Most One Change ([AMOC](https://www.jstor.org/stable/2334932)), and the newer Prune Exact Linear Time ([PELT](https://arxiv.org/pdf/1101.1438.pdf)). Besides being much faster than my previous `pymc3` approach, these methods are also more robust. For instance, I could detect multiple change points in my steps data without fully specifying distributions for them. The particular function you call in `changepoint` depend on whether the data's mean, variance, or both have changed. You then need to specify penalties for calculating the changepoint(s), or have the algorithms calculate them for you. A nice walkthrough of the package is found [here](http://members.cbio.mines-paristech.fr/~thocking/change-tutorial/RK-CptWorkshop.html).

### Modeling & forecasting
Time series data can be modeled in different ways: [Hidden Markov Models](https://en.wikipedia.org/wiki/Hidden_Markov_model)(HMMs), linear Gaussian models with the Kalman filter applied, or Bayesian structures, each having its own strengths and weaknesses. 

For forecasting, extensions to STL could be used (eg. STLM, STLF), or depending on application you can use [Exponential Smoothing](https://pkg.robjhyndman.com/forecast/reference/ets.html) (ETS), [Autoregressive Integrated Moving Average](https://en.wikipedia.org/wiki/Autoregressive_integrated_moving_average) (ARIMA), or [Box-Cox transform, ARMA errors, Trend, and Seasonal](https://robjhyndman.com/papers/ComplexSeasonality.pdf) (BATS/TBATS). 

### Time-series data sources
Since my personal datasets are tiny, it's good to know sources for larger, richer datasets. Along with the well-known Kaggle [time-series datasets](https://www.kaggle.com/tags/time-series), the US Centers for Disease Control sponsors a competition to forecast flu spread at [FluSight](https://predict.cdc.gov/), providing ground truth using actual flu surveillance data along with test sets.

### Reference

Since the field has been around a while, there are many, many books on time-series analysis. A recent one I find interesting is Aileen Nielsen's [Practical Time Series Analysis](https://www.oreilly.com/library/view/practical-time-series/9781492041641/). The writing is very accessible, there are plenty of references, and Nielsen alternated code examples between R and python. I can see this style becoming a little disorienting for some readers, but I actually liked it, since it forces you to focus on the concepts rather than implementation details while giving a good survey of available tools.
