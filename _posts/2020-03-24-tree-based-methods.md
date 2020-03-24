---
layout: post
title: Tree-based methods
---

In prediction and forecasting, the interpretability of the model is often as important as accuracy or recall. This is where decision trees often have an advantage, despite their age, since they're readily interpretable. One notable disadvantage is that trees are usually unstable, and typically have lower accuracy than other methods.

### Extensions to tree-based methods

Starting with the basic regression or classification trees (usually referred together as Classification and Regression Tree, or CART), developments include [CHAID](https://en.wikipedia.org/wiki/Chi-square_automatic_interaction_detection) (Chi-square Automatic Interaction Detection), a non-parametric decision tree incorporating Bonferroni correction for significance testing.

Further developments to address trees' inherent instability include boosted trees, bagged trees (of which [random forest](https://en.wikipedia.org/wiki/Random_forest) is one example), which take some average of multiple trees.
