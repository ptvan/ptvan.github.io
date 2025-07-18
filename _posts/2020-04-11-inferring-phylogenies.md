---
layout: post
title: Inferring phylogenies from genomic data
---

Besides fundamental scientific interest, the phylogeny of infectious pathogens is also important for understanding and thus ultimately controlling the spread of epidemics. This is increasingly important in modern times in light of recurrent outbreaks (eg. MERS, SARS, COVID19). The accessibility of sequencing technologies mean that phylogenies can be rooted in genomic data, often at near [real-time speeds](https://nextstrain.org/).

### Overview

To grossly oversimply things, the basic steps of inferring a phylogeny are:

1. Obtain and format sequence data

2. Perform alignment [[shell code](https://github.com/ptvan/workflows/blob/master/sh/metagenomics_workflow.sh)]

3. Infer a phylogenetic tree [[R code](https://github.com/ptvan/R-snippets/blob/master/phylogenetic_analysis.R)]

4. Assign time scales

### Working with sequence data

In 2020, getting sequence data is very straightforward. There are a number of general sources like [NCBI](https://www.ncbi.nlm.nih.gov/nucleotide/) or [modENCODE](http://www.modencode.org/) and more specific ones like ~~[ViPR](https://www.viprbrc.org/)~~ [BV-BRC](https://www.bv-brc.org/), which focuses on microbes. Handling sequence data is readily supported for both R (through Bioconductor's [Biostrings](https://bioconductor.org/packages/release/bioc/html/Biostrings.html), among others) and Python (through biopython's [Seq](https://biopython.org/wiki/Seq) class).

### Perform sequence alignment

Whether your data is from different species or multiple sampling of the same rapidly-evolving species, the first step in inferring phylogenies is to perform a __multiple sequence alignment__ (MSA). Some of the tools used are [Clustal](http://www.clustal.org/clustal2/), [MAFFT](https://mafft.cbrc.jp/alignment/software/), [parsnp](https://github.com/marbl/parsnp), [minimap](https://github.com/marbl/parsnp) and [mummer](https://mummer4.github.io/).

### Infer phylogenetic trees

Once you have obtained the MSA, you can construct a phylogenetic tree with one of several algorithms: [PHYLIP](https://phylipweb.github.io/phylip/), [IQ-TREE](https://iqtree.github.io/), [RAxML](https://sco.h-its.org/exelixis/web/software/raxml/), or [FastTree](https://morgannprice.github.io/fasttree/). You will need to determine a [substitution model](https://en.wikipedia.org/wiki/Substitution_model) to represent how the sequences evolved in your organism(s), though some tools like IQ-TREE can also do this for you as part of tree construction. For more on substitution models, check out [Paul Lewis](https://phylogeny.uconn.edu/)' excellent primer seminars at the equally excellent [PhyloSeminar](http://phyloseminar.org/recorded.html) repository of talks.

At this stage, it's good to familiarize yourself with the relevant file formats like [NEXUS](https://en.wikipedia.org/wiki/Nexus_file), [PHYLIP](http://rosalind.info/glossary/phylip-format/) and [Newick](https://phylipweb.github.io/phylip/newicktree.html). In R, trees can be stored as `phylo` S3 objects, supported by many phylogenetic packages (eg. [ape](http://ape-package.ird.fr/), [phylobase](https://github.com/fmichonneau/phylobase)). More recently, [treeio](https://guangchuangyu.github.io/software/treeio/) implements in the R4 `treedata` class, which interoperates with the [tidytree](https://cran.r-project.org/web/packages/tidytree/index.html) package, not to be confused with [TidyTree](https://cdcgov.github.io/TidyTree/), a Javascript tree visualization tool from the CDC.

### Phylodynamic modeling

Assigning time scales to branching points, or __phylodynamic__ modeling, can be done using [TreeTime](https://github.com/neherlab/treetime), [Beast2](https://www.beast2.org/) or [LSD](http://www.atgc-montpellier.fr/LSD/). These algorithms operate on a number of file types, `TreeTime`, for example, works on FASTA, PHYLIP, and VCF.

### Visualization

For visualizing and annotating trees with metadata, the `treeio` package readily works with `ggtree`, and the interoperability is [very well documented](https://yulab-smu.github.io/treedata-book/) by their author.

### Acknowledgements

A fairly comprehensive reference is [The Phylogenetic Handbook](https://www.kuleuven.be/aidslab/phylogenybook/home.html). Also, much of the information in this blog post wouldn't be possible without the great bodies of work by my former FredHutch colleagues [Erick Matsen](https://matsen.fhcrc.org/) and [Trevor Bedford](https://bedford.io/). Lastly, my TwinStrand colleague Dan Sommer also gave considerable useful advice.
