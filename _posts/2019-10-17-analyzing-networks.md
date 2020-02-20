---
layout: post
title: Analyzing networks
---

A while back, my labmate Ju showed me a visualization he was working on to explore co-authorships at FredHutch, which reminded me about the many ways to analyze network data. This also inspired me to use [REntrez](https://cran.r-project.org/web/packages/rentrez/index.html) to visualize my much more modest publication network. The [code](https://github.com/ptvan/R-snippets/blob/master/coauthor_network.R) I wrote was intended to show the different research circles I participated in over the years and was fairly straightforward (see below).

### Getting network data

The [Stanford Large Network Dataset Collection](https://snap.stanford.edu/data/) has publicly accessible datasets, as do [KONECT](http://konect.uni-koblenz.de/networks/) and academic groups like [Uri Alon](http://www.weizmann.ac.il/mcb/UriAlon/download/collection-complex-networks) and [Mark Newman](http://www-personal.umich.edu/~mejn/netdata/).

### Network properties

Networks has basic graph properties like [assortativity](https://en.wikipedia.org/wiki/Assortativity) and [clustering coefficient](https://en.wikipedia.org/wiki/Clustering_coefficient). Nodes also have [degree](https://en.wikipedia.org/wiki/Degree_(graph_theory)) and [centrality](https://en.wikipedia.org/wiki/Centrality), which can be measured in several ways. Depending on its _type_ of data, a network can also additional properties brought on by the metadata of the nodes and edges.

### Working with networks in R

First, you have to pick a data format for your graph. The [igraph](https://igraph.org/r/) format is fairly well-known, so that's what I used, and there is [intergraph](https://cran.r-project.org/web/packages/intergraph/) to interconvert between `igraph`, `network` and basic `data.frames` containing nodes and edges.

While `igraph` has plotting capabilities, I personally find its plots unattractive. Instead I used [ggnetwork](https://briatte.github.io/ggnetwork/) and [ggraph](https://github.com/thomasp85/ggraph), which uses Grammar of Graphics syntax (made famous by the now standard [ggplot2](https://ggplot2.tidyverse.org/)), producing this image:
![coauthor-network](/images/coauthor-network.png "coauthor-network.png")

That's good enough for my purposes. But if you need interactivity, [visNetwork](https://datastorm-open.github.io/visNetwork/) is likely what you want.

### Working with networks in Python

[NetworkX](https://networkx.github.io/) is a Python package for network analysis. Since it is cross-platform, you can get also get [iGraph for Python](https://igraph.org/python/).

### References

A fairly academic introduction to networks can be found in [Social and Economic Networks](https://web.stanford.edu/~jacksonm/books.html#book). A more practical reference is [Complex Network Analysis in Python](http://www.networksciencelab.com/).

