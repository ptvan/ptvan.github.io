---
layout: post
title: Linear models
---

Linear models have been around for a long time, and despite attention given to more modern methods, they remain relevant. The principle behind them is easy to understand, though once you look at them rigorously there are a lot to consider. This simplicity means linear models have been extended and built upon for new data types and applications.

**NOTE: linear models is an enormous subject, this post is inevitably incomplete and is also particularly disjointed. Reorganizing and expanding it into something usable and interesting is one of my weekend projects.**

### Basic formulation and extensions

At its core, a linear model assumes that the outcome (both continuous or categorical) is correlated with a linear combination of the predictors. To find the optimal solution, *residuals* are minimized between the predicted value and actual outcome. Ordinary Least Squares (OLS) is a well-known linear regression method that dated back to [Legrendre](https://en.wikipedia.org/wiki/Adrien-Marie_Legendre) and [Gauss](https://en.wikipedia.org/wiki/Carl_Friedrich_Gauss).

More complex linear models can include either `fixed` or `random` effects, or in the case of `mixed-effects`, both.

*Cox proportional hazard* models are survival models that are based on regression. *Time series* data can also be understood and predicted using linear models.

LInear Models for MicroArray (limma) by [Gordon Smythe](https://www.wehi.edu.au/people/gordon-smyth), conceived for microarrays then extended for RNASeq, is used extensively in bioinformatics.

### Selecting predictors in multiple regression

In simple cases, we have a handful of predictors affecting our outcome: for example, predicting salary using age, gender and ethnicity. Here assigning coefficients to each predictor is relatively straightforward. However, we often have data with dozens or hundreds of potential predictors, such as all the genes in a genomic experiment predicting disease status. Picking the "correct" predictors then becomes more challenging.

Generally speaking, we want to avoid overfitting models by using as few predictors as possible while still achieving reasonable accuracy. Assigning penalties, a.k.a. *regularization* can be helpful. **Lasso** ("Least Absolute Shrinkage and Selection Operator") by [Tibshirani](http://statweb.stanford.edu/~tibs/) and [Hastie](https://web.stanford.edu/~hastie/) shrinks the coefficients of certain predictors to zero, keeping other predictors in the model as "important" by assigning a penalty term (thus performing the "selection" function of its name). The lasso penalty term is the sum of the model's coefficients.

Lasso works great if our predictors behave differently from each other, but if they are correlated, it will pick one correlated predictor over another since from its perspective, they are equally likely. Another issue with Lasso comes up when there are more predictors than observations (the so-called *p>n problem*), where Lasso will pick at most *n* predictors and shrink the rest away. An alternative approach is to use a different penalty term, specifically the sum of *squares* of coefficients. This approach, called **ridge regression**, ensures that no predictor ever gets excluded from the model, effectively performing no selection.

In a way, Lasso and ridge regression can be thought of as two extreme solutions to handling coefficients. The **elastic net** strikes a middleground between these extremes, including both penalty terms and solving the *p>n problem*.

### Assessing the performance of your model

It's always good to check the model before accepting the results, since problems could arise the data or violations of the model's assumptions. This applies to modeling in general, not just linear models.

*Outliers* can cause problems by skewing the underlying regression. Plotting the data often reveals the outliers, and there are formal methods for detecting outliers, which can then be dropped. Alternatively, robust regression can be used.

*Heteroscedascity* occurs when the variance of the data is not constant. This causes the estimated standard error to be wrong, which in turn leads to incorrect hypothesis testing and confidence intervals.

*Collinearity* as stated above, causes instability in the coefficients and occurs when one predictor can be predicted by linearly combining other predictors. This can be detected using tests (Condition Number Test, Farrar-Glauber), Variance Inflation Factor, or explicitly testing the stability of the coefficients by perturbing the data with random noise.

It's also a good idea to perform *cross-validation*, dividing your dataset into *training* and *testing* partitions and as they say, rinse and repeat.

### Implementations

Thanks to its roots as a statistical programming language, R has particularly strong support of linear models, a core installation often includes the `stats` package which provides the `lm()` and `glm()` functions. Regularization is supported by the `glmnet` and `elasticnet` packages, among others.

In Python, the `linear_model` module in **scikit-learn** is fairly comprehensive, with OLS, regularization, logistic and GLM. Alternatively, [statsmodels](https://www.statsmodels.org/stable/index.html) also provides these functionalities as well as survival and time series analysis.

### References

Most general statistics books like the now-classic [Modern Applied Statistics with S](https://link.springer.com/book/10.1007/978-0-387-21706-2) and the more modern [An Introduction to Statistical Learning](https://www.statlearning.com/) include sections on linear models (the latter being much more accessible). Among books that focus specifically on linear models, I find [Linear Models with R](https://people.bath.ac.uk/jjf23/LMR/index.html) and [Extending the Linear Model with R](https://people.bath.ac.uk/jjf23/ELM/index.html) from Julian Faraway particularly helpful, though my reading in the field is by no means exhaustive.
