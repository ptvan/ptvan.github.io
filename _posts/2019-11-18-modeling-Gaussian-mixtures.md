---
layout: post
title: Modeling Gaussian mixtures
---

Thanks to R's roots as a statistical programming language it has very strong support for common statistical tasks like modeling and prediction. In modeling your data as a mixture of distributions, there are many R packages, as reviewed by [this paper](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5096736/), and I'm sure more are being developed all the time. I was told by my colleague Chad about `mclust`, which seems to strike a good balance between features, ease-of-use, and speed (thanks Chad!).

### Finding mean step counts using `mclust` 

Analyzing my [iphone step count dataset](https://github.com/ptvan/datasets/tree/master/iphone_health) is pretty straightforward. Absent explicit parameters, `mclust` will pick the number of distributions for you through [BIC](https://en.wikipedia.org/wiki/Bayesian_information_criterion), or you can specify yourself. For density estimation, it is literally a one-liner: 

```r
dens <- densityMclust(steps$stepsWalked)
```
This output has parameters for the component Gaussians, as well as the parameter selection for diagnostic purposes. For my steps data, were 4 components, with approximate mean step counts of 3000, 6000, 10000 and 12000, which I have documented in [modeling_gaussian_mixtures.R](https://github.com/ptvan/R-snippets/blob/master/modeling_gaussian_mixtures.R)

`mclust` can also do clustering and perform cross-validation, and will work on data of higher dimensions (which I suspect is what most people actually use it for). But since my step data is neither very large nor very metadata-rich, there was little more to do.
