---
layout: post
title: Data Visualization in Python
---

Since I have done quite a bit of data cleaning/exploration and visualization over the years, it's worth discussing tools Python has for these tasks. Where the R [Tidyverse](https://www.tidyverse.org/) comes with its own visualization library in form of the well-known [ggplot2](https://ggplot2.tidyverse.org/) package, Python folks are blessed and cursed with options: the old-school [matplotlib](https://matplotlib.org/), the new-school [seaborn](https://seaborn.pydata.org/), the web-oriented [Bokeh](https://docs.bokeh.org/en/latest), as well as a [Python version of ggplot](http://ggplot.yhathq.com/).

## It's good to be polyglot: geographic data in Python

I discussed working with geographic data using R in a [previous blogpost](https://ptvan.github.io/geographic-data-in-R/). Python has [GeoViews](http://geoviews.org/) for handling large-scale maps, part of the [HoloViz](http://holoviz.org)* collection of libraries. 

*_Somewhat confusingly, HoloViz also provides `hvPlot`, which allows general-purpose plotting that partially overlaps with seaborn/matplotlib/ggplot._