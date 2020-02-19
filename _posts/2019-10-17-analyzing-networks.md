---
layout: post
title: Analyzing networks
---

A while back, my labmate Ju showed me a visualization he was working on to explore co-authorships at FredHutch, which reminded me about the many ways to analyze network data. This also inspired me to use [REntrez](https://cran.r-project.org/web/packages/rentrez/index.html) to visualize my much more modest publication network. The [code](https://github.com/ptvan/R-snippets/blob/master/coauthor_network.R) I wrote was intended to show the different research circles I was apart of over the years and was fairly straightforward.

### Working with networks in R

First, you have to pick a data format for your graph. The [igraph](https://igraph.org/r/) format is fairly well-known, so that's what I used, and there is [intergraph](https://cran.r-project.org/web/packages/intergraph/) to interconvert between `igraph`, `network` and basic `data.frames` containing nodes and edges.

Igraph has plotting capabilities but I personally frankly find its plots too plain. Instead I used [ggnetwork](https://briatte.github.io/ggnetwork/) and [ggraph](https://github.com/thomasp85/ggraph), which uses Grammar of Graphics syntax (made famous by the now standard [ggplot2](https://ggplot2.tidyverse.org/)), producing this image:
![coauthor-network](/images/coauthor-network.png "coauthor-network.png")

That's good enough for my purposes. But if you need interactivity, [visNetwork](https://datastorm-open.github.io/visNetwork/) is likely what you want.

