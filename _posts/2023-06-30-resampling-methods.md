---
layout: post
title: Resampling methods and Introduction To The Bootstrap book
---

As humans we all like to have good luck. Professionally however, a "lucky" set of scientific results creates more problems than it solves, giving us false sense of success culminating in a biased view of reality. Whether you work at the wet bench or entirely _in silico_, a common question that comes up in research is: how likely was my results ? I find myself pondering this question often, and decided read up on bootstrapping and write down things I have learned.

Conceptually, resampling is pretty simple: it just means creating new samples by drawing from your existing observation (usually with replacement). Doing this gives you some additional insights into your data in the form of parameter estimates for the population your observation was drawn from. In the case of my "how likely was my results ?" question, the parameter estimate I was looking for was the standard error.

As you may expect, resampling is a lot more complicated than the conceptual explanation above. For example, _jackknife resampling_ only works with "smooth" differentiable statistics like the mean, and shouldn't be used for medians or quantiles. _Cross-validation_ is resampling done on statistical models, eg. resampling regression coefficients as a way to better understand the robustness of your inference, and actually predates the bootstrap. Another consideration is how much we should resample. For point estimates like standard error, as low as 50 bootstrap replications is usually enough, and there are diminishing returns beyond 200 replications. For more complex estimates like confidence intervals, more replications are needed.

I learned a lot by reading "An Introduction to the Bootstrap", published in 1994. Despite having "introduction" in the title the book is very comprehensive, authored by [Bradley Efron](https://statistics.stanford.edu/people/bradley-efron), who invented the bootstrap and [Robert Tibshirani](https://statistics.stanford.edu/people/robert-tibshirani) who was responsible for among other things, LARS/lasso which I touched on in [a previous post](https://ptvan.github.io/linear-models/). The first few chapters of the book covered some general conceptual background like statistical distributions and calculation of standard errors. The simplest version of the bootstrap, estimating standard error, is covered in Chapter 6, with related materials in the next few chapters. Permutation tests are covered in Chapter 15 and cross-validation is discussed in Chapter 17. The index includes a lovely little joke for those who dig in deep.

Resampling methods are also discussed in "An Introduction to Statistical Learning" (whose authors also include Tibshirani), though the coverage is necessarily shorter given that book's broader focus.

### Implementations

In R, the `boot` package includes the `boot()` function which takes as input a function that generates the statistic to be bootstrapped, supports different resampling schemes and multiple CPUs/cores. It also has other functions like `glm.cv()` for GLMs, `boot.ci()` for calculating confidence intervals.

Some time ago, I ran into the package `nptest`, which can use Monte Carlo simulations to perform Standard Error tests.
