---
layout: post
title: The design of experiments
---

Having worked at both the wet bench and in field ecology, I had my fair share of experimental design. At the same time, I have to admit having controls for a PCR or picking field sites is entirely different from designing a complex multi-site vaccine trial or longitudinal studies. As our capacity for larger bench and dry experiments grow, their designs become increasingly important.

### Why experiments

Purely observational studies can be informative, but are subject to biases in observation. Controlling some parts of your experiment enables you to identify and test causal relationships. Most experiments are Simple Comparative Experiments where you're detecting differences between two or more groups, the prototypical of which is a 2-sample [t-test](https://en.wikipedia.org/wiki/Student%27s_t-test).

### Causality and confounding

Causality is a tricky philosophical concept. Thankfully in the smaller scope of experimental design, tools like [Bradford's Criteria](https://en.wikipedia.org/wiki/Bradford_Hill_criteria) help setting up concrete goals.

A _confounder_ is a factor that causes spurious associations in the data by affecting both the dependent and independent variable. An example would be if the experiment looks to compare healthy and sick subjects, but all healthy subjects come from one location and all sick subjects came from another location. In this scenario, location is completely confounded with health status.

There are a number of ways to address confounders. Case-control studies aim to have equal confounders in cases and controls. If confounders are identified after the study has stareted, they can be added as covariates in subsequent analyses.

### Choosing your variables

A common experiment design is to compare means between two or more groups. Your choice of the experiment's outcome affect the type of distribution you would use for modelling the results: counts, continuous or [ipsative](https://en.wikipedia.org/wiki/Ipsative).

### Pseudoreplication

Replication is central to reproducible research. Bench experiments should have both biological and technical replicates, while only the latter is possible for entirely _in silico_ experiments.

The lack of replication is often associated with failed experiments, and when coupled with intent, constitutes scientific fraud. More subtle, and therefore more common is _pseudoreplication_ where the number of replicates is perceived to be higher due to complicated experimental design, as outlined in Stuart Hurlbert's now classic [paper](https://esajournals.onlinelibrary.wiley.com/doi/abs/10.2307/1942661).

### Statistical power

For many experiments, a p-value threshold is established for hypothesis testing, and significance is reported against this threshold. There are some well-documented [mathematical](https://www.nature.com/articles/nature.2016.19503) and [practical](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5738950/) problems with this, but the convention is still held strongly.

For large clinical trials where the incidence of disease is uncertain, statistical power is estimated beforehand to ensure that a certain number of cases occurs.

### More complex designs

An experiment may have more complex designs, like [blocked, or nested](https://online.stat.psu.edu/stat503/lesson/14).  

### References

There are plenty of books on experimental design. On the short side, [Experimental Design for Biologists](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4280443/), which covers reagents and choice of model organisms.
