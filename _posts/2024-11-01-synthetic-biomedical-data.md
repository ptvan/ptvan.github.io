---
layout: post
title: Working with synthetic biomedical data
---

When developing data analysis methods, one major issue is having access to realistic examples to make analyses robust and reproducible. For simple sanity checks, random number generators (with appropriate constraints on range, frequency, _etc._) or [Fisher's Iris dataset](https://en.wikipedia.org/wiki/Iris_flower_data_set) could be enough. But if you need the input to be in a highly specific format with realistic biological variation like biomedical data or electronic health records, simple random number generators are no longer sufficient.

### Generating synthetic genomic data

While there are a number of public repositories for natural genomic data, _eg._ [SRA](https://www.ncbi.nlm.nih.gov/sra) sometimes it's more convenient to generate your own sequencing data directly. For that, [dwgsim](https://github.com/nh13/DWGSIM) provides a way to flexibly generate sequencing reads that can be used as input for read-level tools (_eg._ [fastQC](https://www.bioinformatics.babraham.ac.uk/projects/fastqc/), [fastp](https://github.com/OpenGene/fastp)) or entire genomic pipelines.

### Generating synthetic observational data

The [Observational Medical Outcomes Partnership (OMOP)](https://www.ohdsi.org/data-standardization/) provides a Common Data Model (CDM) for observational data, so compatible SQL tables can be created. OMOP is widely used, but due to obvious privacy concern, OMOP datasets from real subjects aren't usually publicly accessible.

However, _synthetic_ data can be downloaded in bulk, including general, disease- and geography-specific [datasets from Mitre](https://synthea.mitre.org/downloads). These were generated using [Synthea](https://github.com/synthetichealth/synthea), which can create synthetic patients using [different parameters](https://synthetichealth.github.io/spt/#/customizer). Synthea outputs its data in multiple formats, from [FHIR](https://hl7.org/fhir/) JSON to plain CSV. There are even open-source tools such as [ETL-Synthea](https://github.com/OHDSI/ETL-Synthea) to import these CSVs into the OMOP CDM.

### Processing synthetic biomedical data

While many analysis tasks operate on tabular data, often data comes in other formats such as JSON for FHIR. This necessitates creating a data processing step using [additional tools](https://ptvan.github.io/command-line-tools/), though unsurprisingly bespoke tools also exist for R ([fhircrackr](https://github.com/polar-fhir/fhircrackr) or [BiocFHIR](https://bioconductor.org/packages/release/bioc/html/BiocFHIR.html)) and Python ([fhirpack](https://pypi.org/project/fhirpack/) and [fhiry](https://github.com/dermatologist/fhiry)).

### Storage and querying

Depending on the scenario, OMOP and FHIR data can cover thousands of subjects in millions of rows, meriting performance considerations. Previously, [SQLite](https://www.sqlite.org/index.html) has been a popular choice, especially for rapid prototyping, given its cross-platform availability, low overhead, high performance and extensive plugins including those [not requiring external dependencies](https://github.com/nalgeon/sqlean) and [those that do](https://sqlpkg.org/).

However, recently SQLite has been eclipsed by [DuckDB](https://duckdb.org), having not only superior performance, but better support for [languages and data formats](https://dirk-petersen.medium.com/researchers-please-replace-sqlite-with-duckdb-now-f038044a2702), as well as its own [plugin collection](https://github.com/davidgasquez/awesome-duckdb). In fact, if you need synthetic OMOP data and are performing analyses in R, the package [CDMConnector](https://cran.r-project.org/web/packages/CDMConnector/index.html) provides a DuckDB instance containing Synthea-generated OMOP data that allows you to start working almost immediately.
