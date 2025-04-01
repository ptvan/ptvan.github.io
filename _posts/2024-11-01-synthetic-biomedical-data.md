---
layout: post
title: Working with synthetic biomedical data
---

When developing data analysis methods, one major issue is having access to realistic examples to make analyses robust and reproducible. For simple sanity checks, random number generators (with appropriate constraints on range, frequency, _etc._) or [Fisher's Iris dataset](https://en.wikipedia.org/wiki/Iris_flower_data_set) could be enough. But if you need the input to be in a highly specific format with realistic biological variation like biomedical data or electronic health records, simple random generators are no longer sufficient.

### Synthetic genomic data
While there are a number of public repositories for natural genomic data, _eg._ [SRA](https://www.ncbi.nlm.nih.gov/sra) sometimes it's more convenient to generate your own sequencing data directly. For that, [dwgsim](https://github.com/nh13/DWGSIM) provides a way to flexibly generate sequencing reads. 

### Synthetic observational data
[Observational Medical Outcomes Partnership (OMOP)](https://www.ohdsi.org/data-standardization/) provides a Common Data Model for observational data, so compliant DDLs can create SQL tables that are compatible. OMOP is widely used, but due to privacy concerns it's hard to get public OMOP datasets. Instead, [Synthea](https://github.com/synthetichealth/synthea) can generate synthetic patients using [a number of parameters](https://synthetichealth.github.io/spt/#/customizer). Synthea outputs its data in multiple formats, including CSV. There are even open-source tools such as [ETL-Synthea](https://github.com/OHDSI/ETL-Synthea) to import these CSVs into the OMOP CDM. 

### Database backends
Depending on the scenario, OMOP data can cover thousands of subjects in millions of rows, meriting performance considerations. 
Previously, [SQLite](https://www.sqlite.org/index.html) has been a popular choice, especially for rapid prototyping, given its cross-platform availability, low overhead and high performance. However, it has since been eclipsed by [DuckDB](https://duckdb.org) having not only superior performance, but [better support for languages and data formats](https://dirk-petersen.medium.com/researchers-please-replace-sqlite-with-duckdb-now-f038044a2702). In fact, if you need synthetic OMOP data and are performing analyses in R, the package [CDMConnector](https://cran.r-project.org/web/packages/CDMConnector/index.html) provides a DuckDB instance containing Synthea data that allows you to start working almost immediately.
