---
layout: post
title: The design of experiments
---

Having worked at both the wet bench and in field ecology, I had my fair share of experimental design. Though I have to admit having controls for a PCR or picking field sites is a far cry from designing a complex multi-site vaccine trial or longitudinal studies.

### Why experiments

### Choosing your variables

### Replication, real or pseudo

Replication is central to reproducible research. Bench experiments should have both biological and technical replicates, while only the latter is possible for entirely _in silico_ experiments.

The lack of replication is often associated with failed experiments, and when coupled with intent, constitutes scientific fraud. More subtle, and therefore more common is _pseudoreplication_ where the number of replicates is perceived to be higher due to complicated experimental design, as outlined in Stuart Hurlbert's now classic [paper](https://esajournals.onlinelibrary.wiley.com/doi/abs/10.2307/1942661).

### Confounding

A _confounder_ is a factor that causes spurious associations in the data by affecting both the dependent and independent variable. An example would be if the experiment looks to compare healthy and sick subjects, but all healthy subjects come from one location and all sick subjects came from another location. In this scenario, location is completely confounded with health status.

### Statistical power

For many experiments, a p-value threshold is established for hypothesis testing, and significance is reported against this threshold. There are some well-documented issues with this, but the convention is held strongly.

For large clinical trials where the incidence of disease is uncertain, statistical power is estimated before hand to assure that a certain number of cases occurs.

### References

There are plenty of books on experimental design. On the short side, [Experimental Design for Biologists](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4280443/), which covers reagents and choice of model organisms.
