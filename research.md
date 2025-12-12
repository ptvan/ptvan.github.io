---
layout: page
title: 
permalink: /research/
---

My resume is available here: [PhuTVan-resume.pdf](PhuTVan-resume.pdf). If you prefer something more academic and comprehensive, my CV is here: [PhuTVan-CV.pdf](PhuTVan-CV.pdf).

For the more technically inclined, my GitHub repos are located at [https://github.com/ptvan](https://github.com/ptvan).

## Brief executive summary

I'm currently the Bioinformatics Solutions Consultant at [Pluto Biosciences](https://pluto.bio), supporting our multi-omics computational biology platform. Previously I was the Senior Manager of Bioinformatics Solutions at [TwinStrand Biosciences](https://twinstrandbio.com/), specializing on duplex sequencing for mutagenesis and cancer applications. Before that I worked as a postdoc, then an analyst at [Fred Hutch Cancer Center](https://www.fredhutch.org/en/research/divisions/vaccine-infectious-disease-division.html) on flow/mass cytometry and transcriptomics. I received my PhD at [Carnegie Mellon](https://cmu.edu/bio) where I designed and built a patented fluorescence imager to detect low-abundance proteins. Before grad school I worked on gene transcription networks and proteomics at the [Institute for Systems Biology](https://baliga.systemsbiology.net/).

My greatest strength is adaptability: in addition to my career in computational biology, I have had success as [field ecologist](https://www.fs.usda.gov/colville) and [photojournalist](https://makingtheprince.blogspot.com/2013/11/meet-author.html). I am motivated and organized, having worked 3 jobs simultaneously through college and self-published an illustrated children's book through KickStarter in graduate school.

I enjoy explaining and applying complex ideas. I lectured introductory biology to 200 students and mentored 3 undergraduate teams during my PhD, and my professional life involves collaboration with diverse international researchers. Outside my research day job, I'm a strong advocate for science literacy, mentoring students from elementary school through PhD, and curating an open [wiki of data science best practices](https://sciwiki.fredhutch.org).

## Detailed descriptions of major projects

### Multi-omics (2025 - )

I served as the client-facing bioinformatics expert at [Pluto Biosciences](https://pluto.bio). I solved problems in ChIPseq/ATACseq, bulk and single-cell RNASeq and advised customers on bioinformatics and statistics. I also worked closely with the engineering team by creating working prototype pipelines to be productionized, collecting Voice of Customers and creating reproducible bug reports.

### Genomics (2021 - 2024)

I was the subject matter expert for the computational side of [duplex sequencing](https://twinstrandbio.com/technology/), connecting the various departments in the company, and overseeing a team of Bioinformatics Scientists. I co-authored papers with our commercial and academic clients, wrote Application Notes and tutorials, and served as second-line expertise for our tech support department.

Most recently, I analyzed duplex sequencing data for a Liver-On-Chip (LOC) system, deconvolving mutations from the LOC's complex mixture of cell types to remove contamination and assess the system's response to different mutagens. [link to paper](https://www.sciencedirect.com/science/article/abs/pii/S138357182400038X)

![CRL_LOC_MFs](/images/CRL_LOC_MF.jpg "CRL_LOC_MF.jpg")

Another project I worked on compared TwinStrand technology to the transgenic rodent assay (TGR) and the alkaline comet assay for detecting mutations induced by NDEA, a common carcinogen [link to paper](https://www.sciencedirect.com/science/article/pii/S1383571823001031).

![NDEA_simple_spectra](/images/NDEA_simple_spectra.jpg "NDEA_simple_spectra.jpg")

Yet another project I worked on assessed the reproducibility of duplex sequencing across multiple labs [link to paper](https://www.sciencedirect.com/science/article/abs/pii/S1383571823000670).

![HealthCanada_Inotive](/images/HealthCanada_Inotive_trinucleotide.jpg "HealthCanada_Inotive_trinucleotide.jpg")

Finally I worked on compared DuplexSeq's mutagenic detection with the gold-standard *LacZ* test [link to paper](https://pubmed.ncbi.nlm.nih.gov/37341741/).

![MutaMouse_PRC](/images/MutaMouse_PRC_MF.jpg "MutaMouse_PRC_MF.jpg")

I started out in the company as a senior Bioinformatics Scientist, analyzing genomic data for commercial and academic clients, going from aligned reads to variants to modeling outcomes. I was also responsible for presenting findings and addressing post-analysis data requests. A year later, I was promoted to lead the newly-formed Bioinformatics Solutions group within the larger Data Sciences Department, managing a team of Bioinformatics Scientists working on cross-functional projects.

### Transcriptomics (2017 - 2020)

I was the lead analyst on a project with collaborators at the [University of Washington](https://cerid.uw.edu/lab/hawn-lab) to identify genes that contribute to Tuberculosis resistance in African subjects. I performed data QC, genome alignment, transcript quantification, and downstream analyses (DEG, GSEA, functional annotation, network analysis, *etc*) [link to paper](https://www.jci.org/articles/view/140073).

![RSTR_overview](/images/RSTR_overview.jpg "RSTR_overview.jpg")

I also contributed [code](https://github.com/ptvan/r-snippets) to joint workflows and analyses and was a co-author on a follow-up project on the same cohort. [link to paper](https://journals.asm.org/doi/full/10.1128/msphere.00159-22)

My third publication during this period involved some data analysis for the RTS,S/AS01 vaccine for malaria. [link to paper](https://elifesciences.org/articles/70393).

Another project involved collaborators at the [South African Tuberculosis Vaccine Institute](http://www.satvi.uct.ac.za/) to identify possible diagnostic biomarkers for Tuberculosis. I performed my own analyses while also coordinating between Seattle and Cape Town teams in integrating transcriptomic, proteomic and antibody data.

Lastly I also worked on developing a positivity call for Intracellular Cytokine Staining (ICS) data from HIV vaccine trials. The goal of this project is to increase accuracy of the ICS assay while reducing the number of markers required for predicting outcomes.

### Flow cytometry & mass cytometry (2014 - 2018)

As a postdoc, I helped extend [OpenCyto](http://opencyto.org), an open-source R software framework for analyzing high-dimensional flow-cytometry and mass-cytometry data. I also worked on [ggCyto](https://www.bioconductor.org/packages/release/bioc/html/ggcyto.html), an R package that enables ggplot-style plotting of flow- and mass-cytometry datasets. [link to paper](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC6223365/)

![ggCyto](/images/ggcyto-example.jpg "ggcyto-example.jpg")

### Structured Illumination Gel Imager (SIGI) and 2DE proteomics (2009 - 2014)

My PhD contained 3 parts: first, I built a high-dynamic-range imager to detect rare proteins in 2-dimensional electrophoretic (2DE) gels, which we dubbed SIGI. SIGI captured multiple exposures of the 2DE gels containing fluorescently-labelled proteins with structured illumination from an LCD projector and automatically assembled the final 32-bit grayscale images. SIGI also contained a robotic cutting arm that can excise the proteins from the gels for sequencing by tandem mass spectra (MS/MS).  Carnegie Mellon was granted a US [patent](https://patents.google.com/patent/US10362237B2/) on SIGI after I graduated. [link to paper](https://www.ncbi.nlm.nih.gov/pubmed/24935033)

Second, I developed and refined an agarose stacking gel that improved protein retention during the preparation of 2DE gels for MS/MS sequencing. [link to paper](https://www.ncbi.nlm.nih.gov/pubmed/25042010)

Lastly, I mentored three 2-person teams of CMU undergrads in preparing 2DE protein gels, operating the imager and performing data analysis on their experiments.

![SIGI overview](/images/SIGI-operation.jpg "SIGI-operation.jpg")

### Microbial oxidative stress response network (2008 - 2009)

Working at the Institute for Systems Biology (ISB) as a research associate, I worked on an extension for [Inferelator](https://www.ncbi.nlm.nih.gov/pubmed/16686963), an algorithm for predicting regulators of gene expression, implemented in R at the time. This branch of the algorithm ended up being superseded, but you can see what I worked on in [this Github repository](https://github.com/ptvan/inferelator-ancient). This work enabled us to build and test a model of oxidative stress response in the archaeon *Halobacterium salinarum*, which can survive extremely salty environments like Utah's Great Salt Lake. [link to paper](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC1987344/)

![EGRIN_OS network](/images/EGRIN_OS-network.jpg "EGRIN_OS-network.jpg")

### Microbial PeptideAtlas database and web portal (2006 - 2008)

During my internship at ISB, I converted peptide mass spectra of *Halobacterium* experiments from vendor binary formats into mzXML, mapped spectra to peptides then loaded the proteins into SQLServer-backed web [portal](https://peptideatlas.org). We also found biases in peptide detection depending on the sequencing method used. [link to paper](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC2643335/)

![Halobacterium PeptideAtlas](/images/halopeptideatlas-peptidecount.jpg "halopeptideatlas-peptidecount.jpg")

### Geospatial model of rodent spread in Seattle (2006 - 2007)

As part of our Bachelor theses, my University of Washington classmate and good friend Filip and I collected sightings of the rodent [nutria](https://en.wikipedia.org/wiki/Coypu) (*Myocastor coypus*) in western Washington, mainly in the area surrounding Union Bay. I created a linear model to predict the spread of the species in Seattle using R and ArcGIS. This project ended up informing a decision by the UW's Environmental Health and Safety not to undertake eradication efforts, since much of the nutria population was not surviving through the winters anyway.

![UBNA nutria map](/images/UBNA-model.jpg "UBNA-model.jpg")
