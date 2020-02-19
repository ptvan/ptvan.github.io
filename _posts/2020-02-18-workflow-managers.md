---
layout: post
title: Workflow managers for bioinformatic pipelines
---

Due partly to the growth of datasets, and partly to the [replication crisis in science](https://jamanetwork.com/journals/jama/fullarticle/201218), workflow managers have been growing in popularity for bioinformatics. I'd like to say that in bioinformatics, most of the time you have _awkwardly sized_ data, not big enough to warrant Hadoop/Spark and thousands of cores, but painful to handle on any single desktop computer. We often need to re-run analyses with small changes in parameters, or hand analyses off to collaborators. Taken together, certain bioinformatic pipelines benefit from workflow managers.

At FredHutch where I work, the two most common are [Nextflow and Cromwell](https://sciwiki.fredhutch.org/scicomputing/software_overview/#workflow-managers). [Snakemake](https://github.com/snakemake/snakemake) is also popular though I don't have much personal experience with it. 

### NextFlow
[NextFlow](https://www.nextflow.io/) is very portable. You download the Nextflow executable, call it on a script and off you go ! You can mix-and-match languages, which makes it usable for even simple tasks like [converting a bunch of images into JPEGs](https://github.com/ptvan/aws/blob/master/image_processing.nf). 

### Cromwell
[Cromwell](https://github.com/broadinstitute/cromwell) requires a bit more work. You need a database backend to store your jobs that you interface with using a REST API.

