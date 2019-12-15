---
layout: post
title: Imbalanced Data
---

When performing classification, one problem occurs when you have much more data in one class than another (or remaining) class (roughly defined as 4:1 or greater ratio in the binary case). In these scenarios, the [accuracy paradox](https://en.wikipedia.org/wiki/Accuracy_paradox) states that you can get very high accuracy but really your predictions are mostly biased towards the more abundant class.

These scenarios occur fairly often, especially in financial fraud detection. So much so that there is a well-known [Kaggle challenge](https://www.kaggle.com/mlg-ulb/creditcardfraud).

### Approaches for handling imbalanced data

As detailed in several articles ([here](https://machinelearningmastery.com/tactics-to-combat-imbalanced-classes-in-your-machine-learning-dataset/) and [here](https://towardsdatascience.com/methods-for-dealing-with-imbalanced-data-5b761be45a18)), there are multiple ways to deal with imbalanced data:

1. Redefining your metric: accuracy isn't the only thing you can use to measure the performance of a model.

2. Resampling: if you have a lot of data (tens of thousands of rows or more), you could try oversampling the rare class, or alternately, undersampling the abundant class.

3. Generate synthetic data: like resampling, this attempts to shift the balance of the data's classes more to your favor by generating data that is similar to the rare class. There are tools to do this for common languages (see below)

4. Penalized models: impose costs on mistaken prediction, pushing your predictions away from the majority class

5. Try a different approach like anomaly/change detection.  

### Tools for handling imbalanced data

1. SMOTE (Synthetic Minority Oversampling TEchnique) is implemented in R and Python.
