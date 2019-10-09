---
layout: post
title: MCMC in Python on iPhone health data
---

I recently ran across the excellent book [Bayesian Methods for Hackers](https://www.amazon.com/Bayesian-Methods-Hackers-Probabilistic-Addison-Wesley/dp/0133902838/). Since my phone has been tracking my running (via RunKeeper)
and biking (via Strava), I thought this may be a fun dataset to play around with.

It was fairly straightforward to extract the XML from the iPhone's Health app, parse it and do some minor [cleaning](https://github.com/ptvan/R-snippets/blob/master/parse_apple_health_export.R).

From there it wasn't too hard to model some distributions using the `pymc3` package: exponential for each &lambda; representing the step count before and after a hypothesized shift in activity level, and &tau; for the actual time of the shift. I put the results in here: [python-snippets](https://github.com/ptvan/python-snippets/blob/master/mcmc.py). 