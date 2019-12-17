---
layout: post
title: Imbalanced Data
---

When performing classification, one problem occurs when you have much more data in one class than another class (roughly defined as 4:1 or greater ratio in the binary case). In these scenarios, the [accuracy paradox](https://en.wikipedia.org/wiki/Accuracy_paradox) states that you can get very high accuracy but really your predictions are mostly biased towards the more abundant class.

These scenarios occur fairly often in certain fields, like customer surveys since the vast majority of people don't fill out the forms, or financial fraud detection since the majority of purchases are legitimate. In fact, there is a well-known [Kaggle challenge](https://www.kaggle.com/mlg-ulb/creditcardfraud).

### Approaches for handling imbalanced data

As discussed both [informally](https://machinelearningmastery.com/tactics-to-combat-imbalanced-classes-in-your-machine-learning-dataset/) and more [academically](https://link.springer.com/article/10.1007/s13748-016-0094-0), there are multiple ways to deal with imbalanced data:

- *Reframing the problem*: This could involve changing your performance metrics. Accuracy isn't the only thing you can use to measure the performance of a model. There are also [F-scores](https://en.wikipedia.org/wiki/F1_score), [Cohen's &kappa;](https://en.wikipedia.org/wiki/Cohen%27s_kappa), etc. Alternatively, you can decompose the larger class into smaller classes, which can then be paired against the minority class using ensemble classifiers. Alternatively, you can treat the scenario like outlier detection and using [one-class classifiers](https://en.wikipedia.org/wiki/One-class_classification). 

- *Data-level methods*: If you have a lot of data (tens of thousands of rows), you could try oversampling the rare class, or undersampling the abundant class. Or you could generate new data for the rare class. Like resampling, this attempts to shift the balance of the classes to your favor by generating data that is similar to the rare class. There are mature algorithms for this (see below).

- *Algorithm-level methods*: This involves imposing costs on mistaken prediction using penalized models, pushing your predictions away from the majority class.


### Tools for handling imbalanced data

For oversampling, R has, among others, the [smotefamily](https://cran.r-project.org/web/packages/smotefamily/index.html) package. Python has the [imbalanced-learn](https://pypi.org/project/imbalanced-learn/) package. Both R and Python implements the oversampling algorithms below:

- SMOTE (Synthetic Minority Oversampling TEchnique) was presented in a [2002 JAIR paper](https://www.jair.org/index.php/jair/article/view/10302), which has a nice explanation [here](http://rikunert.com/SMOTE_explained). SMOTE generates additional samples of rare class by selecting their K-nearest neighbors.

- ADASYN (Adaptive Synthetic Sampling), published in [2008](https://sci2s.ugr.es/keel/pdf/algorithm/congreso/2008-He-ieee.pdf) builds upon SMOTE. More data is generated for minority class samples that are harder to learn, trying to make your predictions more robust.   

On the other hand, ROSE (Random Over-Sampling Examples), published in [2012](https://link.springer.com/article/10.1007/s10618-012-0295-5), and implemented in the [ROSE](https://cran.r-project.org/web/packages/ROSE/) R package, uses both over- and under-sampling.