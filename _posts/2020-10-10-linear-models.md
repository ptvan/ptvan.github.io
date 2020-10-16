---
layout: post
title: Linear models
---

Linear models have been around for a long time, and despite the press given to more modern methods, they remain relevant. The principle behind them is easy to understand, though once you look at them rigorously there are a lot to consider. This simplicity means linear models can be extended and built upon for new data types and applications.

### Basic formulation

At its core, a linear model assumes that the output can is correlated with a linear combination of the input. To find the optimal solution, errors is minimized between the predicted and actual output.

### A little history

Least squares linear regression have been known to [Legrendre](https://en.wikipedia.org/wiki/Adrien-Marie_Legendre) and [Gauss](https://en.wikipedia.org/wiki/Carl_Friedrich_Gauss).

### Model diagnostics

It's always good to check the model before accepting the results since problems could arise either from the data, or violation of the model's assumptions.

*Collinearity* causes instability in the coefficients and occurs when one predictor can be predicted by linearly combining other predictors. This can be detected using tests (Condition Number Test, Farrar-Glauber), Variance Inflation Factor, or explicitly testing the stability of the coefficients by perturbing the data with random noise.

### Extensions to the linear model

A natural extension to basic linear regression is logistic regression.

*Cox proportional hazard* models are survival models that are based on regression.

*Regularization* can be helpful when too many predictors are present in the input. Least angle regression (LARS), by [Tibshirani](http://statweb.stanford.edu/~tibs/) and [Hastie](https://web.stanford.edu/~hastie/) shrinks the coefficients of certain predictors to zero, performing variable selection on the fly.

Notable in the bioinformatic space is [Gordon Smythe](https://www.wehi.edu.au/people/gordon-smyth)'s LInear Models for MicroArray (limma) conceived for microarrays, extended for RNASeq, with many refinements along the way.

### Implementations

Thanks to its roots as a statistical programming language, R has particularly strong support of linear models, with `stats::lm()` normally built as part of a core installation.

In Python, the `linear_model` module in scikit-learn is fairly extensive, with OLS, regularization, logistic and GLM.

### References

There are plenty of books on linear models, though I find [Linear Models with R](https://people.bath.ac.uk/jjf23/LMR/index.html) and [Extending the Linear Model with R](https://people.bath.ac.uk/jjf23/ELM/index.html) from Julian Faraway particularly helpful.
