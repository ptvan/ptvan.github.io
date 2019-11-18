---
layout: post
title: Modeling Gaussian mixtures
---

Thanks to R's roots as a statistical programming language it has very strong support for common statistical tasks like modeling and prediction. In modeling your data as a mixture of distributions, there are many R packages, as reviewed by [this paper](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5096736/), and I'm sure more are being developed all the time. I was told by my colleague Chad about `mclust`, which seems to strike a good balance between features, ease-of-use, and speed (thanks Chad!).

It was very straightforward to deconvolve my [iphone step count dataset](https://github.com/ptvan/datasets/tree/master/iphone_health) into Gaussian mixtures:

### Using `mclust` to model Gaussian mixtures

- It is literally a one-liner to do density estimation with `mclust`: 
```
dens <- densityMclust(steps$stepsWalked)
```
