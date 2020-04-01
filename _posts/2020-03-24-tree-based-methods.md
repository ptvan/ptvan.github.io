---
layout: post
title: Tree-based methods
---

In prediction and forecasting, the understandability of the model is often as important as accuracy or recall. This is where despite their age, decision trees often have an advantage, since they're readily interpretable and are often used in clinical and operation management contexts.

### Basic regression or classification trees (CART)

These are the classic implementations, reported in the 1950s but the ideas of branching decision-making likely dated back much further. These implementations have several disadvantages. One, trees are usually unstable, with changes in data often generating entirely different trees. Two, trees typically have lower accuracy than other methods. Three, naively implemented trees do not scale very well. In any case, the `rpart` package allows straightforward regression and classification in R, with pruning and cross-validation.

### Refinements and extensions

More recent developments to CART include [CHAID](https://en.wikipedia.org/wiki/Chi-square_automatic_interaction_detection) (Chi-square Automatic Interaction Detection), a non-parametric decision tree incorporating Bonferroni correction for significance testing.

To address trees' inherent instability include boosted trees, and bagged trees which take some average of multiple trees.[Random forest](https://en.wikipedia.org/wiki/Random_forest), an example of bagged trees, is implemented in the R package of the same name.
