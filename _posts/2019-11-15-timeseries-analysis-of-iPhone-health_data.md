---
layout: post
title: Time-series analysis of iPhone health data
---

I had exported biking distance, running distance and step counts from my iPhone in a
[previous post](https://ptvan.github.io/Python-MCMC-nuggets/). In that post, I tried to detected a supposed change in step count, using `pymc3` to model two different distributions. That was a valid, but rather simplistic approach. Since my step count has fairly good periodicity (and presumably is also a [stationary process](https://en.wikipedia.org/wiki/Stationary_process)), it's better to use time-series analysis.

### The R time-series analysis ecosystem
The relevant data structures are base R's `ts` (time-series), `xts` (extended time-series) and `zoo`. The major packages are `lubridate` (mostly for cleaning and extracting times and dates), `zoo`, and `forecast`. For those interested in stock prediction/quantitative finance, there is `tidyquant`, which speaks xts and zoo, while interoperating with more domain-specific packages (`quantmod`, `PerformanceAnalytics`, etc..) and wrapped up in a Tidyverse user experience.

### Common tasks
These are found in my [timeseries_analysis.R](https://github.com/ptvan/R-snippets/blob/master/timeseries_analysis.R):

- Handling time/dates, which are made straightforward with lubridate and `dplyr`
- Decomposing data into seasonal, trend, and irregular components 


### Reference

Since it's not exactly a new field, there are many, many books on time-series analysis. A recent one I find interesting is Aileen Nielsen's [Practical Time Series Analysis](https://www.oreilly.com/library/view/practical-time-series/9781492041641/). The writing is very accessible, there are plenty of references, and Nielsen alternated code examples between R and python. For some this could be a little disorienting, but I actually kind of liked it, since it showcases multiple tools.
