---
layout: post
title: My favorite ggplot extensions
---

One of my favorite pieces of software is [ggplot2](https://ggplot2.tidyverse.org/): it implements a useful tool based on elegant principles, has reasonable defaults and great extensibility. So great is this extensibility that sometimes it's a little hard to keep track of the many, many software packages ggplot2 has inspired. Below are some of the ggplot2-related packages that I used regularly, ranging from packages that I rediscover from [very old notes](https://ptvan.github.io/LaTeX-notetaking) to more modern packages that I have used recently. This post may be updated as I discover more packages.

### Extending basic ggplot2 functionality: ggrepel, patchwork, cowplot

One of the strengths of ggplot is useful defaults. However, like any general purpose tool aimed to work most of the time for most people, there are invariably special use cases where the default settings do not work. Since anyone can write an extension, many packages inspired by different workflows have been create. [ggrepel](https://ggrepel.slowkow.com/) allows more fine-grained control over text labels, which becomes necessary for large datasets where the labels can get overwhelming or illegible. Composing a figure made up of multiple ggplot outputs is a common use case, which inspired [patchwork](https://patchwork.data-imaginist.com/articles/patchwork.html). Certain ggplot options are used so frequently that they are bundled together, such as the excellent [cowplot](https://github.com/wilkelab/cowplot), in the fine R tradition of the ["miscellaneous" package](https://cran.r-project.org/web/packages/Hmisc/index.html).

### New graphical primitives and plot types: ggally, ggdendro, ggridges, ggmap, ggradar, et al.

Probably the most numerous category, these packages implement graphics that would be time-consuming or even impossible to create in base ggplot2 using built-in primitives like `geom_point` or `geom_line`. 

Some of my favorites include [ggally](https://ggobi.github.io/ggally/) actually enables multiple new plot types: pairwise plot matrix, survival plot, and functions to plot networks. Dendrograms can be drawn using [dendextend](https://github.com/talgalili/dendextend) which superseded the older `ggdendro`. Ridgeline plots can be made using [ggridges](https://wilkelab.org/ggridges/articles/introduction.html) from the Wilke lab which also originated the excellent `cowplot` above. Maps can be drawn using [ggmap](https://github.com/dkahle/ggmap) though personally I've always found handling maps in R to be unwieldy compared to a [full-blown GIS](https://ptvan.github.io/analyzing-geographic-data/) (admittedly an unfair comparison). If you need to draw radar charts, [ggradar](https://github.com/ricardo-bion/ggradar) is a go-to. 

### Interactivity: gganimate, ggiraph

Sometimes it's useful to make plots that are interactive without being [full-blown dashboards](https://ptvan.github.io/Python-interactive-dataviz/). At a basic level, animations consisting of multiple graphic frames can be create to compare data over time. These animations can be made as `.gif`s or even video files, using [gganimate](https://gganimate.com/). If you need full-interactivity (_eg._ mouseovers), [ggiraph](https://github.com/davidgohel/ggiraph) can provide this functionality.

### Statistical annotations: ggpubr, ggstatplot

Not surprisingly, many ggplot users are academics, or otherwise people who support reproducible research. This means that often you need to display p-values or show which comparisons are being made across different experiment groups. 