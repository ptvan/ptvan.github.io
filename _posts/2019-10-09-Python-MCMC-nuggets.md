---
layout: post
title: Python MCMC nuggets
---

I recently ran across the excellent book [Bayesian Methods for Hackers](https://www.amazon.com/Bayesian-Methods-Hackers-Probabilistic-Addison-Wesley/dp/0133902838/) and worked through variants of the exercises. I've put the relevant code [here](https://github.com/ptvan/python-snippets/blob/master/pymc3.py). Detailed notes are below.

### Modelling a change in iPhone daily step count

Since my phone has been tracking my running (via RunKeeper) and biking (via Strava), I thought these may be good real datasets to play around with.

It was fairly straightforward to extract the XML from the iPhone's Health app, [parse it](https://github.com/ptvan/R-snippets/blob/master/parse_apple_health_export.R) and save as a [dataset](https://github.com/ptvan/datasets/tree/master/iphone_health).

From there it wasn't too hard to model some distributions using the `pymc3` package: exponential for each &lambda; representing the step count before and after a hypothesized shift in activity level, and &tau; for the actual time of the shift. However, if I only wanted to detect when a change occurred in the step count data, building a full model is an overkill. It's better to simply use time-series methods like [outlier or changepoint detection](https://ptvan.github.io/timeseries-analysis-of-iPhone-health_data).

### Detecting students who cheat on tests

This example is a little bit more complicated. Now we're delving a little deeper in PyMC, defining a `Deterministic variable` using a `Theano` tensor. PyMC underwent an API change in version 3, but the steps are still the same. This is a bigger project, so the results weren't instantaneous as like the previous project. But then again, I was running on my ancient Linux desktop without a GPU, so the Theano back-end was not perfoming optimally. My mid-2014 MacBookPro performed only marginally better, with the added complication of [missing header files in OSX Mojave](https://stackoverflow.com/questions/52509602/cant-compile-c-program-on-a-mac-after-upgrade-to-mojave). 

