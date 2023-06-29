---
layout: post
title: The design of experiments
---

Having started out in field ecology, done some work at the bench then transitioned to computational biology, I had my fair share of exposure to experimental design. From the relatively simply task of having controls for PCR reaction, to picking sites for a field survey, to designing a complex multi-site vaccine trial, as our capacity for larger experiments grow, their designs become increasingly important. In a perfect world, every experiment would be carefully designed before being carried out, but reality is often sadly messier.

### Why experiments

Purely observational studies can be informative, but are subject to biases in observation. Controlling some parts of your experiment enables you to identify and test causal relationships. Many experiments are Simple Comparative Experiments where you're detecting differences between two or more groups, the prototypical of which is a 2-sample [t-test](https://en.wikipedia.org/wiki/Student%27s_t-test).

### Causality and confounding

Finding causal relationships in experiments is tricky, and proving them is hard, as evidenced by sayings both [old](https://en.wikipedia.org/wiki/Post_hoc_ergo_propter_hoc) and [new](https://en.wikipedia.org/wiki/Correlation_does_not_imply_causation). "Correlation does not imply causation" exists because correlation is abundant and is often tantalizingly suggestive. Looking at John Snow's famous map of Broad Street cholera outbreak(https://en.wikipedia.org/wiki/John_Snow#Cholera), the location of the fabled water pump at the center of the outbreak is very striking and indeed removing the infected pump's handle coincided with the outbreak's decline, but the [causal chain and timing of events were more complex](https://en.wikipedia.org/wiki/1854_Broad_Street_cholera_outbreak#Investigation_by_John_Snow).

Scientists have developed conceptual tools for assessing causality over the years, from [Hill's Criteria](https://en.wikipedia.org/wiki/Bradford_Hill_criteria) in epidemiology to [Koch's Postulates](https://en.wikipedia.org/wiki/Koch%27s_postulates) in microbiology, but proving causality in the supposedly controlled environment of scientific experiments remain fraught. Certain fields have their own technical complications over correlation, such as [functional magnetic resonance imaging](https://pubmed.ncbi.nlm.nih.gov/26158964/).

A _confounder_ is a factor that causes spurious associations in the data by affecting both the dependent and independent variables. An simple example: your experiment compares healthy and sick subjects, but all healthy subjects come from one location and all sick subjects came from another location. In this scenario, location is completely confounded with health/sick status.

There are some ways to address confounders. Case-control studies aim to have equal confounders in cases and controls. If confounders are identified after the study has started, they can be added as covariates in subsequent analyses.

### Choosing your variables

A common experiment design is to compare means between two or more groups. Your choice of the experiment's outcome affect the type of distribution you would use for modelling the results: counts, continuous or [ipsative](https://en.wikipedia.org/wiki/Ipsative).

### Pseudoreplication

Replication is central to reproducible research. Bench experiments should have both biological and technical replicates, but only technical replicates is possible for entirely _in silico_ experiments.

The lack of replication is often associated with failed experiments, and when coupled with intent, constitutes scientific fraud. More subtle, and therefore more common is _pseudoreplication_ where the number of replicates is perceived to be higher due to complicated experimental design, as outlined in Stuart Hurlbert's now-classic [Pseudoreplication and the Design of Ecological Field Experiments](https://esajournals.onlinelibrary.wiley.com/doi/abs/10.2307/1942661).

### Statistical power

For many experiments, a p-value threshold is established for hypothesis testing, and significance is reported against this threshold. There are some well-documented [mathematical](https://www.nature.com/articles/nature.2016.19503) and [practical](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5738950/) problems with this, but the reliance on p-values still exist in many fields

For large clinical trials where the incidence of disease is uncertain, statistical power is estimated beforehand to ensure that a certain number of cases occurs.

### More complex designs

An experiment may have more complex designs, like [blocked, or nested](https://online.stat.psu.edu/stat503/lesson/14).  

### References

There are plenty of books on experimental design. On the short side, [Experimental Design for Biologists](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4280443/), which covers reagents and choice of model organisms.
