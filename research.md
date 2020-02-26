---
layout: page
title: 
permalink: /research/
---

My resume is located here: [PhuTVan-resume.pdf](PhuTVan-resume.pdf)

# A brief summary

I'm currently an analyst at [Fred Hutch](http://rglab.org), working in flow/mass cytometry, RNASeq and genomics. I received my PhD at [Carnegie Mellon](https://cmu.edu/bio) where I designed and built a patented fluorescence imager to detect low-abundance proteins. Before grad school I worked on gene transcription networks and proteomics at the [Institute for Systems Biology](https://baliga.systemsbiology.net/). 

My greatest strength is adaptability: prior to working as an analyst, I have had success as [field ecologist](https://www.fs.usda.gov/colville), [photojournalist](https://makingtheprince.blogspot.com/2013/11/meet-author.html) and bioengineer. I am motivated and organized, having worked 3 jobs simultaneously through college and self-published an illustrated children's book through KickStarter in graduate school. 

I enjoy explaining and applying complex ideas. I lectured introductory biology to 200 students and mentored 3 undergraduate teams during my PhD, and am currently collaborating with a diverse international team of researchers. Outside my research day job, I'm a strong advocate for science literacy, mentoring students from elementary school through PhD, and curating an open [wiki of data science best practices](https://sciwiki.fredhutch.org).

# Detailed descriptions of major projects

### Transcriptomics and genomics (2017 - )
I've been lead analyst on a project with collaborators at the [University of Washington](https://www.washington.edu/) to identify genes that contribute to Tuberculosis resistance in African subjects. I performed data QC, genome alignment, transcript quantification, as well as downstream analyses (DEG, GSEA, functional annotion, network analysis, etc.). I contributed code to [RNASeq workflows](https://github.com/rglab/rnaseqpipeliner) and [analyses](https://github.com/ptvan/r-snippets). I've begun work on integrating genomic data for this project.

Another project involves collaborators at the [South African Tuberculosis Vaccine Institute](http://www.satvi.uct.ac.za/) to identify possible diagnostic biomarkers for Tuberculosis. I perform my own analyses while also coordinating between Seattle and Cape Town teams in integrating transcriptomic, proteomic and antibody data. 

My third project involves developing a positivity call for Intracellular Cytokine Staining (ICS) data from HIV vaccine trials. The goal of this project is to increase accuracy of the ICS assay while reducing the number of markers required.

### Flow cytometry (2014 - 2018)
As a postdoc, I helped extend [OpenCyto](http://opencyto.org), an open-source R software framework for analyzing high-dimensional flow-cytometry and mass-cytometry data. I also worked on ggCyto, an R package that enables ggplot-style plotting of flow- and mass-cytometry datasets. [paper](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC6223365/)

![ggCyto](/images/ggcyto-example.jpg "ggcyto-example.jpg")

### Structured Illumination Gel Imager (SIGI) and 2DE protein gels (2009 - 2014)
My PhD contained 3 parts: first, I built a high-dynamic-range imager to detect rare proteins in 2-dimensional electrophoretic (2DE) gels, which we dubbed SIGI. SIGI captured multiple exposures of the 2DE gels containing fluorescently-labelled proteins with structured illumination from an LCD projector and automatically assembled the final 32-bit grayscale images. SIGI also contained a robotic cutting arm that can excise the proteins from the gels for sequencing by tandem mass spectra (MS/MS).  Carnegie Mellon was granted a US [patent](https://patents.google.com/patent/US10362237B2/) on SIGI after I graduated. [paper](https://www.ncbi.nlm.nih.gov/pubmed/24935033)

Second, I developed and refined a agarose gel that improved protein retention during the preparation of 2DE gels for MS/MS sequencing. [paper](https://www.ncbi.nlm.nih.gov/pubmed/25042010)

Lastly, I mentored three 2-person teams of CMU undergrads in preparing 2DE protein gels, operating the imager and performed data analysis on the output.

![SIGI overview](/images/SIGI-operation.jpg "SIGI-operation.jpg")

### Archeal oxidative stress response network (2008 - 2009)
Working at the Institute for Systems Biology (ISB) as a research associate, I worked on an extended version of [Inferelator](https://www.ncbi.nlm.nih.gov/pubmed/16686963), an algorithm for predicting regulators of gene expression at the time implemented in R. This branch of the algorithm ended up being superseded, but you can see what I worked on in this Github [repository](https://github.com/ptvan/inferelator-ancient). This work enabled us to build and test a model of oxidative stress response in an extremophilic archaeon. [paper](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC1987344/) 

![EGRIN_OS network](/images/EGRIN_OS-network.jpg "EGRIN_OS-network.jpg")

### Halobacterium PeptideAtlas (2006 - 2008)
During my internship at ISB, I converted peptide mass spectra from vendor-specific binary formats into mzXML, mapped spectra to peptides then loaded the proteins into SQLServer-backed web [portal](https://peptideatlas.org). We also found biases in peptide detection depending on the method used. [paper](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC2643335/). 

![Halobacterium PeptideAtlas](/images/halopeptideatlas-peptidecount.jpg "halopeptideatlas-peptidecount.jpg")

### Nutria spread in Seattle (2006 - 2007)
As University of Washington undergrads, my good friend Filip and I collected sightings of [nutria](https://en.wikipedia.org/wiki/Coypu) (Myocastor coypus) in western Washington, mainly in areas surrounding Union Bay. I ran a linear model to predict the spread of the species in Seattle using R and ArcGIS. This ended up informing a decision by the UW's Environmental Health and Safety not to undertake eradication efforts, since much of the population was not surviving through the winters anyway. 

![UBNA nutria map](/images/UBNA-model.jpg "UBNA-model.jpg")