---
layout: post
title: Workflow managers for bioinformatic pipelines
---

Due to the growth of data, workflow managers (_eg._ [Airflow](https://airflow.apache.org/), [Prefect](https://www.prefect.io/)) have been growing in popularity. In bioinformatics this popularity is further accelerated by the [replication crisis in science](https://jamanetwork.com/journals/jama/fullarticle/201218). Workflow managers automate routine tasks while also ensuring reproducibility by enabling drop-in changes in data, runtime parameters, or even entire toolchains. At Fred Hutch where I used to work, [Nextflow and Cromwell](https://sciwiki.fredhutch.org/scicomputing/software_overview/#workflow-managers) were most popular. Elsewhere, [Snakemake](https://github.com/snakemake/snakemake) is also popular though I don't have much personal experience with it.

### Nextflow

[Nextflow](https://www.nextflow.io/) is based on an extended version of [Groovy](http://groovy-lang.org) and is now on the second version. My former colleague [Sam Minot](https://www.minot.bio/) set up the FredHutch [Nextflow demos](https://github.com/FredHutch/nf-core-aligngenomes) leveraging his background in viral metagenomics.

Simple tasks like batch-converting PNGs into JPEGs only took me a [few minutes](https://github.com/ptvan/workflows/blob/master/nextflow/image_processing.nf). Writing a simple [DataCarpentry genomic workflow](https://datacarpentry.org/wrangling-genomics/) into Nextflow DSL2 is a [weekend project](https://github.com/ptvan/workflows/tree/master/wrangling_genomics).

### Cromwell

[Cromwell](https://github.com/broadinstitute/cromwell) has a bit more infrastructure. Workflows use the [Workflow Description Language](https://openwdl.org/) (WDL) but the syntax is also pretty simple and there is a [linting tool](https://cromwell.readthedocs.io/en/stable/WOMtool/) for troubleshooting. Running Cromwell requires a database backend to store jobs that you interface with using a [Swagger](https://swagger.io/) REST API. As a result, the logs are fairly detailed, which aids troubleshooting when jobs fail. My colleague Amy Paguirigan has done much work for supporting Cromwell at FredHutch, having developed [wrapper code](https://github.com/fredhutch/fh.wdlr) and relevant [documentation](https://sciwiki.fredhutch.org/compdemos/Cromwell/). She also put together some workflows to perform [variant calling on RNASeq data](https://github.com/FredHutch/tg-wdl-RNAseqVariantCalling), and pointed us to the Broad Institute's big repository of [GATK-based workflows](https://github.com/gatk-workflows).
