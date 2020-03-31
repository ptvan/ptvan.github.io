---
layout: post
title: Tree-based methods
---

In prediction and forecasting, the understandability of the model is often as important as accuracy or recall. This is where despite their age, decision trees often have an advantage, since they're readily interpretable and are often used in clinical and operation management contexts.

### Basic regression or classification trees (CART)

These are the classic implementations, reported in the 1950s but the ideas of branching decision-making likely dated back much further. These implementations have several disadvantages. One, trees are usually unstable, with changes in data often generating entirely different trees. Two, trees typically have lower accuracy than other methods. Three, naively implemented trees do not scale very well.

### Refinements and extensions

More recent developments to CART include [CHAID](https://en.wikipedia.org/wiki/Chi-square_automatic_interaction_detection) (Chi-square Automatic Interaction Detection), a non-parametric decision tree incorporating Bonferroni correction for significance testing.

To address trees' inherent instability include boosted trees, bagged trees (of which [random forest](https://en.wikipedia.org/wiki/Random_forest) is one example), which take some average of multiple trees.
