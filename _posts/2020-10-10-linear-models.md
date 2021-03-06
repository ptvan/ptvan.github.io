---
layout: post
title: Linear models
---

Linear models have been around for a long time, and despite the press given to more modern methods, they remain relevant. The principle behind them is easy to understand, though once you look at them rigorously there are a lot to consider. This simplicity means linear models can be extended and built upon for new data types and applications.

### A little history

Least squares linear regression have been known to [Legrendre](https://en.wikipedia.org/wiki/Adrien-Marie_Legendre) and [Gauss](https://en.wikipedia.org/wiki/Carl_Friedrich_Gauss).

### Basic formulation

At its core, a linear model assumes that the output (presumably a continuous value) can is correlated with a linear combination of the input. To find the optimal solution, residuals are minimized between the observed output and predicted values.

Statistical models can model either `fixed` or `random` effects, or in the case of `mixed-effects`, both.

### Model diagnostics

It's always good to check the model before accepting the results, since problems could arise either from the data or violations of the model's assumptions.

*Outliers* can cause problems by skewing the underlying regression. Plotting the data often reveals the outliers, and there are formal methods for detecting outliers, which can then be dropped. Alternatively, robust regression can be used.

*Heteroscedascity* occurs when the variance of the data is not constant. This causes the estimated standard error to be wrong, which in turn leads to incorrect hypothesis testing and confidence intervals.

*Collinearity* causes instability in the coefficients and occurs when one predictor can be predicted by linearly combining other predictors. This can be detected using tests (Condition Number Test, Farrar-Glauber), Variance Inflation Factor, or explicitly testing the stability of the coefficients by perturbing the data with random noise.

### Extensions to the linear model

A natural extension to basic linear regression to perform hypothesis testing, comparing two different explanatory models of the data.

Another natural extension is logistic regression, predicting two categorical outcomes.

*Cox proportional hazard* models are survival models that are based on regression.

*Regularization* can be helpful when too many predictors are present in the input. Least angle regression (LARS), by [Tibshirani](http://statweb.stanford.edu/~tibs/) and [Hastie](https://web.stanford.edu/~hastie/) shrinks the coefficients of certain predictors to zero, performing variable selection on the fly.

Notable in the bioinformatic space is [Gordon Smythe](https://www.wehi.edu.au/people/gordon-smyth)'s LInear Models for MicroArray (limma) conceived for microarrays, extended for RNASeq, with many refinements along the way.

### Implementations

Thanks to its roots as a statistical programming language, R has particularly strong support of linear models, with `stats::lm()` normally built as part of a core installation. The `glmnet` package handles regularization using the LARS/Lasso approach as well as the newer elastic net.

In Python, the `linear_model` module in scikit-learn is fairly comprehensive, with OLS, regularization, logistic and GLM. Alternatvely, [statsmodels](https://www.statsmodels.org/stable/index.html) also provides these functionalities as well as survival and time series analysis.

### References

There are plenty of books on linear models, though I find [Linear Models with R](https://people.bath.ac.uk/jjf23/LMR/index.html) and [Extending the Linear Model with R](https://people.bath.ac.uk/jjf23/ELM/index.html) from Julian Faraway particularly helpful.
