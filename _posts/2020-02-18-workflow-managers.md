---
layout: post
title: Workflow managers for bioinformatic pipelines
---

Due partly to the growth of datasets, and partly to the [replication crisis in science](https://jamanetwork.com/journals/jama/fullarticle/201218), workflow managers have been growing in popularity for bioinformatics. Workflow managers automate routine tasks while also enabling small changes in parameters or data, ensuring reproducibility. At FredHutch where I work, the two most common are [Nextflow and Cromwell](https://sciwiki.fredhutch.org/scicomputing/software_overview/#workflow-managers). [Snakemake](https://github.com/snakemake/snakemake) is also popular though I don't have much personal experience with it. 

### NextFlow
[NextFlow](https://www.nextflow.io/) is very portable. You download the Nextflow executable, call it on a script and off you go ! You can mix-and-match languages, and the nextflow language is fairly intuitive if you have done any programming at all. Simple tasks like converting a bunch of images into JPEGs only took me a [few minutes](https://github.com/ptvan/aws/blob/master/image_processing.nf). Due to its lightweight nature, you don't get much information when things fail.

### Cromwell
[Cromwell](https://github.com/broadinstitute/cromwell) has a bit more infrastructure. Running Cromwell requires a database backend to store jobs that you interface with using a REST API. Cromwell uses its own [Workflow Description Language](https://openwdl.org/) (WDL) but the syntax is also fairly straightforward and there is a [linting tool](https://cromwell.readthedocs.io/en/stable/WOMtool/) for troubleshooting. When Cromwell jobs fail, the logs are fairly detailed.

### Acknowledgements
My colleague Amy has done much work for adopting Cromwell at FredHutch, including developing [wrapper code](https://github.com/fredhutch/fh.wdlr), [demos](https://github.com/FredHutch/tg-wdl-RNAseqVariantCalling) and relevant [documentation](https://sciwiki.fredhutch.org/compdemos/Cromwell/).
