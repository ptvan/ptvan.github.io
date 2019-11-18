---
layout: post
title: Modeling Gaussian mixtures
---

Thanks to R's roots as a statistical programming language it has very strong support for common statistical tasks like modeling and prediction. In modeling your data as a mixture of distributions, there are many R packages, as reviewed by [this paper](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5096736/), and I'm sure more are being developed all the time. I was told by my colleague Chad about `mclust`, which seems to strike a good balance between features, ease-of-use, and speed (thanks Chad!).

It was very straightforward to deconvolve my [iphone step count dataset](https://github.com/ptvan/datasets/tree/master/iphone_health) into Gaussian mixtures:

### Using `mclust` to model Gaussian mixtures

- Absent explicit parameters, `mclust` will pick the number of distributions for you through [BIC](https://en.wikipedia.org/wiki/Bayesian_information_criterion), or you can specify yourself. For density estimation, it is literally a one-liner: 
{% highlight r %}
dens <- densityMclust(steps$stepsWalked)
{% endhighlight %}
- `mclust` can also do clustering and perform cross-validation.
