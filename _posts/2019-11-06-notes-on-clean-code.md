---
layout: post
title: Notes on clean code and Clean Code (the book) 
---

I'm making my way through Robert C. Martin's classic [Clean Code](http://cleancoder.com/products) book. I won't do an exhaustive summary since there are already many great summaries out there (here's [one](https://gist.github.com/wojteklu/73c6914cc446146b8b533c0988cf8d29), just my general thoughts.

* The [replication crisis](https://jamanetwork.com/journals/jama/fullarticle/201218) likely results, at least in part from the way analysis pipelines are developed in the life sciences. Since biological experiments are expensive, and the pressure to publish is high, bioinformatics code can be more prone to bad practices, with little external corrective pressure. That's not to say that there aren't efforts to make bioinformatic code cleaner, there are in fact several: [TidyVerse](https://www.tidyverse.org/) and [PyData](https://pydata.org/) come to mind.

* In a similar vein, there isn't much incentive to create re-usable software components. Fortunately for common data types like gene expression, there are some common data structures, tools and workflows in place, most notably [BioConductor](https://www.bioconductor.org/). 

* As the saying goes, [naming is hard](https://carlalexander.ca/importance-naming-programming/). 

