---
layout: post
title: Python MCMC nuggets
---

I recently ran across the excellent book [Bayesian Methods for Hackers](https://www.amazon.com/Bayesian-Methods-Hackers-Probabilistic-Addison-Wesley/dp/0133902838/) and worked through versions of the exercises.

### Modelling a change in iPhone daily step count
Since my phone has been tracking my running (via RunKeeper)
and biking (via Strava), I thought this may be a fun dataset to play around with.

It was fairly straightforward to extract the XML from the iPhone's Health app, parse it and do some minor [cleaning](https://github.com/ptvan/R-snippets/blob/master/parse_apple_health_export.R).

From there it wasn't too hard to model some distributions using the `pymc3` package: exponential for each &lambda; representing the step count before and after a hypothesized shift in activity level, and &tau; for the actual time of the shift. I put the results in [here](https://github.com/ptvan/python-snippets/blob/master/mcmc_iphone_stepcounts.py). 

### Detecting students who cheat on tests
This example is a little bit more complicated. Now we're delving a little deeper in PyMC, defining a `Deterministic variable` using a `Theano` tensor. PyMC underwent a bit of an API change in version 3, but the steps are still the same. This is a bigger project, so the MCMC sampling wasn't instantaneous as it was for the previous project (but then again, I was running on my ancient desktop without a GPU, so the Theano back-end was not perfoming optimally). The results are [here](https://github.com/ptvan/python-snippets/blob/master/mcmc_detecting_cheaters.py). 
 

