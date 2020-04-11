---
layout: post
title: Inferring phylogenies
---

Besides fundamental scientific interest, the phylogeny of infectious pathogens is also important for understanding and thus ultimately controlling the spread of epidemics. This is increasingly important in modern times in light of recurrent outbreaks (eg. MERS, SARS, COVID19). The accessibility of sequencing technologies mean that phylogenies can be rooted in genomic data, often at near [real-time speeds](https://nextstrain.org/).

### Overview

The basic steps of inferring a phylogeny are:

1. Obtain and format sequence data

2. Perform alignment

3. Infer a phylogenetic tree

4. Assign time scales (phylodynamic modelling)

### Working with sequence data

In 2020, getting sequence data is very straightforward given. There are a number of general sources like [NCBI](https://www.ncbi.nlm.nih.gov/nucleotide/) or [modENCODE](http://www.modencode.org/) and more specific ones like [ViPR](https://www.viprbrc.org/). Handling sequence data is readily supported for both R (through Bioconductor's [Biostrings](https://bioconductor.org/packages/release/bioc/html/Biostrings.html), among others) and Python (through biopython's [Seq](https://biopython.org/wiki/Seq) class).

### Perform sequence alignment

### Infer phylogenetic trees

### Phylodynamic modeling
