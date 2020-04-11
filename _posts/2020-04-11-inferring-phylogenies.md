---
layout: post
title: Inferring phylogenies
---

Besides fundamental scientific interest, the phylogeny of infectious pathogens is also important for understanding and thus ultimately controlling the spread of epidemics. This is increasingly important in modern times in light of recurrent outbreaks (eg. MERS, SARS, COVID19). The accessibility of sequencing technologies mean that phylogenies can be rooted in genomic data, often at near [real-time speeds](https://nextstrain.org/).

### Overview

The basic steps of inferring a phylogeny are:

1. Obtain and format sequence data

2. Perform alignment [[shell code](https://github.com/ptvan/workflows/blob/master/metagenomics_workflow.sh)]

3. Infer a phylogenetic tree [[R code](https://github.com/ptvan/R-snippets/blob/master/phylogenetic_trees_snippets.R)]

4. Assign time scales (phylodynamic modelling)

### Working with sequence data

In 2020, getting sequence data is very straightforward. There are a number of general sources like [NCBI](https://www.ncbi.nlm.nih.gov/nucleotide/) or [modENCODE](http://www.modencode.org/) and more specific ones like [ViPR](https://www.viprbrc.org/). Handling sequence data is readily supported for both R (through Bioconductor's [Biostrings](https://bioconductor.org/packages/release/bioc/html/Biostrings.html), among others) and Python (through biopython's [Seq](https://biopython.org/wiki/Seq) class).

### Perform sequence alignment

Whether your data is from different species or multiple sampling of the same rapidly-evolving species, the first step in inferring phylogenies is to perform a __multiple sequence alignment__ (MSA). Some of the tools used are [Clustal](http://www.clustal.org/clustal2/) and the newer [MAFFT](https://mafft.cbrc.jp/alignment/software/).

### Infer phylogenetic trees

Once you have obtained the MSA, you can construct a phylogenetic tree with one of several algorithms: [IQ-TREE](http://www.iqtree.org/), [RAxML](https://sco.h-its.org/exelixis/web/software/raxml/), or [FastTree](http://www.microbesonline.org/fasttree/). You will need to determine a [substitution model](https://en.wikipedia.org/wiki/Substitution_model) to represent how the sequences evolved in your organism(s), though some tools like IQ-TREE can also do this for you as part of tree construction. For more on substitution models, check out [Paul Lewis](https://phylogeny.uconn.edu/)' excellent primer seminars at the equally excellent [http://phyloseminar.org/recorded.html](PhyloSeminar) repository of talks.

### Phylodynamic modeling

Assigning time scales to branching points, or __phylodynamic__ modeling, can be done using [treetime](https://github.com/neherlab/treetime).

### Acknowledgements

Much of the information in this blog post wouldn't be possible without the great bodies of work by my FredHutch colleagues [Erick Matsen](https://matsen.fhcrc.org/) and [Trevor Bedford](https://bedford.io/).
