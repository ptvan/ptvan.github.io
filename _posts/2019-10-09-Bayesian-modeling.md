---
layout: post
title: Bayesian modeling in your favorite language(s)
---

When I was in college, the division between Bayesian and frequentist statistics seemed significant (pun maybe intended). Perhaps it seemed that way because of this [2012 book](https://www.amazon.com/Theory-That-Would-Not-Die/dp/0300188226) or this [2014 NYTimes article](https://www.nytimes.com/2014/09/30/science/the-odds-continually-updated.html) ? Interestingly, for just as long, there have been rebuttals, that a "Bayesian vs. frequentist" mindset is not [productive](https://simplystatistics.org/2014/10/13/as-an-applied-statistician-i-find-the-frequentists-versus-bayesians-debate-completely-inconsequential/) or [practical](https://noahpinionblog.blogspot.com/2013/01/bayesian-vs-frequentist-is-there-any.html). I generally tend to agree with these rebuttals, that you should understand the data and use the right tool for the job. 

### STAN (C/C++)
The classic software for Bayesian statistics is [STAN](https://mc-stan.org/). Though written in C, it has a wide range of language APIs, including Python and R (more below). The documentation is excellent, there are a collection of [case studies](https://mc-stan.org/users/documentation/case-studies.html) to get beginners started.

### R 
Since R is a statistical language, [RStan](https://mc-stan.org/rstan/) is logical and inevitable. In fact, the set of worked examples above are dominated by the number of `rstan` use cases. The popular [Doing Bayesian Data Analysis](https://www.amazon.com/Doing-Bayesian-Data-Analysis-Tutorial/dp/0124058884/ref=dp_ob_title_bk) book is now in its second edition, though it's by no means the only `rstan` book.

### Python
The newer, sexier way to do Bayesian modeling in Python is `pymc3`, which feels more Pythonic. It is covered by the excellent book [Bayesian Methods for Hackers](https://www.amazon.com/Bayesian-Methods-Hackers-Probabilistic-Addison-Wesley/dp/0133902838/), which has interesting examples.

Since my phone has been tracking my running (via RunKeeper) and biking (via Strava), I thought these may be good real datasets to play around with.It was fairly straightforward to extract the XML from the iPhone's Health app, [parse it](https://github.com/ptvan/R-snippets/blob/master/parse_apple_health_export.R) and save as a [dataset](https://github.com/ptvan/datasets/tree/master/iphone_health).

From there it wasn't too hard to model some distributions using the `pymc3` package: exponential for each &lambda; representing the step count before and after a hypothesized shift in activity level, and &tau; for the actual time of the shift. However, if I only wanted to detect when a change occurred in the step count data, building a full model is an overkill. It's better to simply use time-series methods like [outlier or changepoint detection](https://ptvan.github.io/timeseries-analysis-of-iPhone-health_data).

The next example involves detecting students who cheat on tests. Now we're delving a little deeper in PyMC, defining a `Deterministic variable` using a `Theano` tensor. PyMC underwent an API change in version 3, but the steps are still the same. This is a bigger project, so the results weren't instantaneous as like the previous project. But then again, I was running on my ancient Linux desktop without a GPU, so the Theano back-end was not perfoming optimally. My mid-2014 MacBookPro performed only marginally better, with the added complication of [missing header files in OSX Mojave](https://stackoverflow.com/questions/52509602/cant-compile-c-program-on-a-mac-after-upgrade-to-mojave). 

