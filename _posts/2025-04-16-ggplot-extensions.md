---
layout: post
title: My favorite ggplot2 extensions
---

One of my favorite pieces of software is [ggplot2](https://ggplot2.tidyverse.org/): it implements a useful tool based on elegant design principles, has reasonable defaults and great extensibility. So great is this extensibility that sometimes it's a little hard to keep track of the many, many software packages ggplot2 has inspired. Below are some of the ggplot2-related packages that I used regularly, ranging from packages that I rediscover from [very old notes](https://ptvan.github.io/LaTeX-notetaking) to more modern packages that I have used recently. This post may be updated as I discover more packages.

### Extending basic ggplot2 functionality: ggrepel, gghighlight, patchwork, cowplot

One of the strengths of ggplot2 is useful defaults aimed to work most of the time for most people. However, there are inevitably special use cases where the default settings do not work. Since anyone can write an R extension, many ggplot-style packages inspired by different use cases have been created. [ggrepel](https://ggrepel.slowkow.com/) allows more fine-grained control over text labels, necessary for large datasets where the labels can get overwhelming or illegibly dense. Similarly, [gghighlight](https://yutannihilation.github.io/gghighlight/articles/gghighlight.html) lets you draw attention to certain elements of a complex plot without having to specify styles for each element manually. Composing a figure made up of multiple ggplot2 graphics is a common task, which inspired [patchwork](https://patchwork.data-imaginist.com/articles/patchwork.html). 

Certain ggplot2 tweaks are used so frequently that they are bundled together, such as in the excellent [cowplot](https://github.com/wilkelab/cowplot), in the fine R tradition of the ["miscellaneous" package](https://cran.r-project.org/web/packages/Hmisc/index.html).

### New graphical primitives and plot types: ggally, ggdendro, ggridges, ggmap, ggradar, et al.

Probably the most numerous category, these packages implement graphics that would be time-consuming or even impossible to create in base ggplot2 using built-in primitives like `geom_point` or `geom_line`. 

Some of my favorites are: [ggally](https://ggobi.github.io/ggally/), which actually enables _multiple_ new plot types: pairwise plot matrix, survival plot, and functions to plot networks. Dendrograms can be drawn using [dendextend](https://github.com/talgalili/dendextend) which superseded the older `ggdendro`. Ridgeline plots can be made using [ggridges](https://wilkelab.org/ggridges/articles/introduction.html) from the Wilke lab which also created the excellent `cowplot` above. Geographic maps can be drawn using [ggmap](https://github.com/dkahle/ggmap), though personally I've always found processing map data in R to be unwieldy compared to a [full-blown GIS](https://ptvan.github.io/analyzing-geographic-data/) (admittedly an unfair comparison). If you need to draw radar charts, [ggradar](https://github.com/ricardo-bion/ggradar) is a good option. I also enjoy [ggbump](https://github.com/davidsjoberg/ggbump) which illustrates rankings (also known as _bumpcharts_) over time very elegantly. Visually similar but conceptually very different are alluvial plots, handled by [ggalluvial](https://r-charts.com/flow/ggalluvial/).

### Interactivity: gganimate, ggiraph

Sometimes it's useful to make plots that are interactive without being [full-blown dashboards](https://ptvan.github.io/Python-interactive-dataviz/). At the simplest level, animations can be created from multiple static graphics to compare data over time. Using [gganimate](https://gganimate.com/) , these animations can be saved as `.gif`s or even video files. If you need full-interactivity (_eg._ mouseovers), [ggiraph](https://github.com/davidgohel/ggiraph) can be used.

### Statistical annotations: ggpubr, ggstatsplot

Not surprisingly, many ggplot2 users are academics, or otherwise people who support reproducible research. This means that often we need to make "publication quality" figures, or at the very least display p-values or show which comparisons are being made across different experiment groups. Many of these annotations can be done using [ggpubr](https://rpkgs.datanovia.com/ggpubr/). If you need even more statistical annotations, such as the model(s) that were used to generate the plot, [ggstatsplot](https://indrajeetpatil.github.io/ggstatsplot/) will calculate stats prior to annotating the plots, streamlining the process.