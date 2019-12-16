---
layout: post
title: Imbalanced Data
---

When performing classification, one problem occurs when you have much more data in one class than another (or remaining) class (roughly defined as 4:1 or greater ratio in the binary case). In these scenarios, the [accuracy paradox](https://en.wikipedia.org/wiki/Accuracy_paradox) states that you can get very high accuracy but really your predictions are mostly biased towards the more abundant class.

These scenarios occur fairly often in certain fields, like financial fraud detection. In fact, there is a well-known [Kaggle challenge](https://www.kaggle.com/mlg-ulb/creditcardfraud).

### Approaches for handling imbalanced data

As detailed in several articles ([here](https://machinelearningmastery.com/tactics-to-combat-imbalanced-classes-in-your-machine-learning-dataset/) and [here](https://towardsdatascience.com/methods-for-dealing-with-imbalanced-data-5b761be45a18)), there are multiple ways to deal with imbalanced data:

1. Redefining your metric: accuracy isn't the only thing you can use to measure the performance of a model. There are also [F-scores](https://en.wikipedia.org/wiki/F1_score), [Cohen's &kappa;](https://en.wikipedia.org/wiki/Cohen%27s_kappa), etc.

2. Resampling: if you have a lot of data (tens of thousands of rows), you could try oversampling the rare class, or alternately, undersampling the abundant class. Caveats are that oversampling increases the possibility of overfitting, while undersampling could potentially leave out information useful for your model.

3. Generate synthetic data: like resampling, this attempts to shift the balance of the classes to your favor by generating data that is similar to the rare class. There are mature algorithms for this (see below).

4. Penalized models: impose costs on mistaken prediction, pushing your predictions away from the majority class.

5. Try a different approach. You can decompose the larger class into smaller classes, which can then be paired against the minority class using ensemble classifiers. Alternatively, you can treat the scenario like outlier detection and using [one-class classifiers](https://en.wikipedia.org/wiki/One-class_classification). 

### Tools for handling imbalanced data

R has, among others, the [smotefamily](https://cran.r-project.org/web/packages/smotefamily/index.html) package. Python has the [imbalanced-learn](https://pypi.org/project/imbalanced-learn/) package, which implements the algorithms below:

- SMOTE (Synthetic Minority Oversampling TEchnique) was presented in a [2002 JAIR paper](https://www.jair.org/index.php/jair/article/view/10302), which has a nice explanation [here](http://rikunert.com/SMOTE_explained). SMOTE generates additional samples of rare class by selecting their K-nearest neighbors.

- ADASYN (Adaptive Synthetic Sampling), published in [2008](https://sci2s.ugr.es/keel/pdf/algorithm/congreso/2008-He-ieee.pdf) builds upon SMOTE. More data is generated for minority class samples that are harder to learn, trying to make your predictions more robust.   