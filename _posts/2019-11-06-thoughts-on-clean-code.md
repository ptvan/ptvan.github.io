---
layout: post
title: Thoughts on clean code and Clean Code book
---

I'm making my way through Robert C. Martin's classic [Clean Code](http://cleancoder.com/products) book. I won't do an exhaustive summary since there are already many great summaries out there (here's [one](https://gist.github.com/wojteklu/73c6914cc446146b8b533c0988cf8d29)), just my general thoughts.

* The [replication crisis](https://jamanetwork.com/journals/jama/fullarticle/201218) likely results, at least in part from the way analysis pipelines are developed in the life sciences. Since biological experiments are expensive, and the pressure to publish is high, bioinformatics code can be more prone to bad practices, with little external corrective pressure. That's not to say that there aren't efforts to make bioinformatic code cleaner, there are in fact several: [TidyVerse](https://www.tidyverse.org/) and [PyData](https://pydata.org/) come to mind.

* In a similar vein, there isn't much incentive to create re-usable software components. Fortunately for common data types like gene expression, there are some common data structures, tools and workflows in place, most notably [BioConductor](https://www.bioconductor.org/).

* As the saying goes, [naming is hard](https://carlalexander.ca/importance-naming-programming/), probably because it depends on the personality (and mood) of the programmer. I inherited one project where a file was named `ihatethis.dat` and another where all the variables were band names. In the latter case, having to explain to a supervisor why `bowie` and `ramones` were failing was funny the first time, and less so the second time.

* Inheriting unclean code poses additional problems. Even when refactoring is obviously beneficial, sometimes the cost is too high. Inheritors of problematic code are often bound by dependencies, like when the code is exported as an API.

* I recognize the benefits of deleting code rather than commenting it out, but sometimes it's useful to have a record of what was previously done, especially if the code performs exploratory analysis.

* I wholly support the idea of self-documenting (self-evident?) code, rather than excessive comments, which can break the reading flow. Then again, when the code is in a highly-specialized domain, some brief background wouldn't hurt.

* I wonder if some of the problems mentioned are brought on at least in part, because of the additional syntactic and implementation overhead of Java and C/C++, the languages used in the book. Even Martin himself suggested this in his [blog post on Clojure](http://blog.cleancoder.com/uncle-bob/2019/08/22/WhyClojure.html).