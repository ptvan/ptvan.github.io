---
layout: post
title: Multimodal Data Integration
---

As the cost of high-throughput biological assays fall, it has become more common to perform _multimodal data integration_, where different assays are performed on the same subjects and/or experimental conditions and the data analyzed together. The assumption is that such integrations would give us additional confidence on the biological insights, or perhaps even discover new ones.

### Assumptions and caveats

Data integration presumes that the sum is better than its parts. For example, suppose you have an experiment where cells are treated with a drug, along with an unexposed control, and transcript and proteome data are collected. In the transcriptomic data, you see a number of genes being over-expressed in the treated group. Similarly in the proteomic data, you see the proteins from these genes also being over-expressed in the treated cells. So the two datasets are responding in the same direction: the exposed cells are up-transcribing some genes, then all those transcripts are being made into more proteins compared to the control.

However, it's just as likely that the response in the two datasets are **not** in the same direction, at least not across all features (matched gene-protein in this case). Maybe only 80% of the up-regulated genes have increased protein counts, while the remaining have similar counts, or maybe even decreased protein counts. What does that mean ?

It is important to ensure that the conclusions you are drawing are not confounded by biological or statistical problems. Some questions to ask yourself:

- Were the samples processed in comparable ways across different assays ? Were all samples processed identically within the same assay ?
- Do the assays have the same sensitivity and dynamic range ? A large change in one assay may be undetectable in the other.
- Are the datasets normalized in the same way ? Are the same samples/features outliers in both datasets ?
- Do the timescales make sense ? Biological processes take time but many experiments are snapshots of cell states and your sampling may have missed the response. 

If you have ruled all these problems out, _perhaps_ your data has generated some new insights.

### Approaches and implementations

There are multiple ways to integrate data from multiple assays. In order of increasing sophistication:

#### Conceptual overlap

This approach involves simply comparing individual genes or proteins that share the same function and/or response across different datasets. Many of the assumptions and caveats above apply.

#### Manually modeling the datasets together

The conceptual overlap approach above isn't very sophisticated. For example, we only get _which_ predictors may be relevant, not their relative _importance_. This can be addressed by manually specifying a linear model that covers both datasets, which would also give you quantitative results like confidence intervals and p-values. The usual modeling caveats of picking the correct underlying distributions, data normalization and scaling, and correctly specifying covariates apply. 

#### Factor analysis

The final approach models the variance explained by the different datasets as _latent factors_, conceptually similar to [principal component analysis](https://en.wikipedia.org/wiki/Principal_component_analysis). There are multiple software packages that implement this: [mCIA](https://www.bioconductor.org/packages/release/bioc/html/omicade4.html), [MOFA](https://github.com/bioFAM/MOFA2), [SPEAR](https://bitbucket.org/kleinstein/spear) and [Seurat](https://satijalab.org/seurat/articles/integration_introduction.html), originally conceived to analyze single-cell RNASeq data. Similar to PCA, one caveat of this approach is that the factors explains the data _numerically_, and it can difficult to assign them _biological_ meaning.