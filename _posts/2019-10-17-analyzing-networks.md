---
layout: post
title: Analyzing networks
---

A while back, my labmate Ju showed me a visualization he was working on to explore co-authorships at FredHutch, which reminded me about the many ways to analyze network data. This also inspired me to use [REntrez](https://cran.r-project.org/web/packages/rentrez/index.html) to visualize my much more modest publication network. The [code](https://github.com/ptvan/R-snippets/blob/master/coauthor_network.R) I wrote was intended to show the different research circles I participated in over the years and was fairly straightforward (see below).

### Getting network data

The [Stanford Large Network Dataset Collection](https://snap.stanford.edu/data/) has publicly accessible datasets, as do [KONECT](http://konect.uni-koblenz.de/networks/) and academic groups like [Uri Alon](http://www.weizmann.ac.il/mcb/UriAlon/download/collection-complex-networks) and [Mark Newman](http://www-personal.umich.edu/~mejn/netdata/).

### Network properties

Networks has basic graph properties like [assortativity](https://en.wikipedia.org/wiki/Assortativity) and [clustering coefficient](https://en.wikipedia.org/wiki/Clustering_coefficient). Nodes also have [degree](https://en.wikipedia.org/wiki/Degree_(graph_theory)) and [centrality](https://en.wikipedia.org/wiki/Centrality), which can be measured in several ways. Depending on its _type_ of data, a network can also have additional properties brought on by the metadata of the nodes and edges, which you can query and model on.

### Working with networks

First, you have to get your data into a format amenable to network analysis. The simplest is a table containing nodes and edges, which most software can parse. If you have a lot of network data, you may want to use a graph database like [Neo4J](https://neo4j.com/). For ease of manipulation graph data, you may want to consider [tidygraph](https://github.com/thomasp85/tidygraph), which uses syntax inspired by the [tidyverse](https://www.tidyverse.org/).

For programmatic access, the cross-platform [igraph](https://igraph.org/r/) library is fairly well-known and has its own data structure. If you're working in R there is [intergraph](https://cran.r-project.org/web/packages/intergraph/) to interconvert between `igraph`, `network` and basic `data.frames` of nodes and edges. While `igraph` has plotting capabilities, I personally find its plots unattractive. Instead I used [ggnetwork](https://briatte.github.io/ggnetwork/) and [ggraph](https://github.com/thomasp85/ggraph), which uses Grammar of Graphics syntax (made famous by the now standard [ggplot2](https://ggplot2.tidyverse.org/)), producing this image for my co-authorship network:
![coauthor-network](/images/coauthor-network.png "coauthor-network.png")

That's good enough for my purposes. But if you need interactivity, [visNetwork](https://datastorm-open.github.io/visNetwork/) is likely what you want. A collection of R network analysis packages is maintained and documented at [statnet](https://statnet.org).

For Python, [NetworkX](https://networkx.github.io/) is fairly mature package. For quick interactive explorations, you can also use [gephi](https://gephi.org/) and/or [Cytoscape](https://cytoscape.org/).

### Performance considerations

Depending on how big and complex your network is, you may want to create a subgraph, work on it before applying changes to the entire dataset. You can also choose to work with the edge and/or node attributes in tabular format before applying them to the network.

### References

A fairly academic introduction to networks can be found in the book [Social and Economic Networks](https://web.stanford.edu/~jacksonm/books.html#book). A more practical book is [Complex Network Analysis in Python](http://www.networksciencelab.com/). The aforementioned `statnet` maintains a collection of tutorials on their [Github page](https://github.com/statnet/Workshops/wiki) that includes both theory and R-specific examples.
