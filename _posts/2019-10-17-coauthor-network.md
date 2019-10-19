---
layout: post
title: Visualizing Co-authorship networks
---


My labmate Ju showed me a visualization he was working on that explored co-authorships at FredHutch, which inspired me to use [REntrez](https://cran.r-project.org/web/packages/rentrez/index.html) to visualize my much more modest publication network.

There are many ways to visualize these types of data. The [code](https://github.com/ptvan/R-snippets/blob/master/coauthor_network.R) I wrote was intended to show the different research circles I was apart of over the years and was fairly straightforward.

### Graph data formats

First, you have to pick a data format for your graph. The [igraph](https://igraph.org/r/) format is fairly well-known, so that's what I used, and there is [intergraph](https://cran.r-project.org/web/packages/intergraph/) to interconvert between `igraph`, `network` and basic data.frames containing nodes and edges.

### Visualizing graphs in R

Igraph has plotting capabilities but I personally frankly find its plots too plain. Instead I used [ggnetwork](https://briatte.github.io/ggnetwork/) and [ggraph](https://github.com/thomasp85/ggraph), which uses Grammar of Graphics syntax (made famous by the now standard [ggplot2](https://ggplot2.tidyverse.org/)), producing this image:
![coauthor-network](/images/coauthor-network.png "coauthor-network.png")

That's good and familiar enough for me. But if you need interactivity, [visNetwork](https://datastorm-open.github.io/visNetwork/) is likely what you want.
