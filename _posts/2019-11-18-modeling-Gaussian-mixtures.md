---
layout: post
title: Modeling Gaussian mixtures
---

Thanks to R's roots as a statistical programming language it has very strong support for common statistical tasks like modeling and prediction. In modeling your data as a mixture of distributions, I know of the `mixtools` package, though there are many others, as reviewed by [this paper](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5096736/), and presumably more are being developed all the time. I was told by my colleague Chad about `mclust`, which seems to strike a good balance between features, ease-of-use, and speed (thanks Chad!).

### Finding mean step counts using `mclust` 

Analyzing my [iphone step count dataset](https://github.com/ptvan/datasets/tree/master/iphone_health) is pretty straightforward. For density estimation, it is literally a one-liner: 

```r
dens <- densityMclust(steps$stepsWalked)
```
Absent explicit parameters, `mclust` will pick the number of distributions for you through [BIC](https://en.wikipedia.org/wiki/Bayesian_information_criterion), or you can specify yourself (eg. `G=10` for exactly 10 clusters, the default is `G=1:9`) 

The output contains parameters for the component Gaussians, as well as the parameter selection for diagnostic purposes. For my steps data, the algorithm found 4 component univariate Gaussians, with approximate mean step counts of 3000, 6000, 10000 and 12000, which I have documented in [modeling_gaussian_mixtures.R](https://github.com/ptvan/R-snippets/blob/master/modeling_gaussian_mixtures.R)

`mclust` also works on data of higher dimensions with the same syntax, which I applied on the merged biking and step count data . It can also do dimensional reduction, do clustering/discriminant analysis and perform cross-validation. But since my step data is neither very large nor very metadata-rich, there was little more to do.

### What about in Python ?

`Scikit-learn` has the `neighbors.KernelDensity` class for the simple [1D case](https://scikit-learn.org/stable/auto_examples/neighbors/plot_kde_1d.html#sphx-glr-auto-examples-neighbors-plot-kde-1d-py), where you can specify different kernels. For modeling higher dimensions, `mixture` provides good [infrastructure](https://scikit-learn.org/stable/modules/mixture.html): you can specify the covariance type as well as the number of expected clusters. For [model selection](https://scikit-learn.org/stable/auto_examples/mixture/plot_gmm_selection.html) you can use either BIC or [AIC](https://en.wikipedia.org/wiki/Akaike_information_criterion) as metrics. The `mixture.GaussianMixture()` call itself returns means and the appropriate covariance matrices, which you can use to make [diagnostic plots](https://www.visiondummy.com/2014/04/geometric-interpretation-covariance-matrix/).
