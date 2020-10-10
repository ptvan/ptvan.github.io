---
layout: post
title: Tree-based regression and classification
---

In prediction and forecasting, the understandability of the model is often as important as accuracy or recall. Decision trees split up the solution space with each branching point. Despite their age, decision trees often have an advantage in interpretability, since branch points are associated with particular thresholds (or classes) in the input data. As a result, decision trees are often used in clinical and operation management contexts.

### Basic classification and regression trees (CART)

These are the classic implementations, reported in the 1950s but the ideas of branching decision-making likely dated back much further. Conceptually, ways to partition data grows rapidly with increasing data. Classic trees implement recursive binary splitting, a greedy approach that makes the best split at every branch point. However, this allows for the possibility of an adequate early split that precludes a much better later split. This problem is addressed with pruning, where a very large tree is grown, then a subtree is selected with cross-validation.

These classic implementations have several disadvantages. One, trees are usually unstable, with changes in data often generating entirely different trees. Two, trees typically have lower accuracy than other methods. Three, naively implemented trees do not scale very well. 

### Refinements and extensions

Refinemenents to CART include [CHAID](https://en.wikipedia.org/wiki/Chi-square_automatic_interaction_detection) (Chi-square Automatic Interaction Detection), a non-parametric decision tree incorporating Bonferroni correction for significance testing.

Enhancements that take some average of multiple trees to address instability of a single tree include boosted trees and bagged trees. [Random forest](https://en.wikipedia.org/wiki/Random_forest), an example of bagged trees, combines results from subtrees into a single predictor. In classification, a majority vote is used, in regression an average is returned.

### Implementations

The `rpart` package allows straightforward regression and classification in R, with pruning. Random Forest is implemented in the R package of the same name. Among other things, `randomForest` will return the relative importance of the input predictors, to be used in variable selection.

