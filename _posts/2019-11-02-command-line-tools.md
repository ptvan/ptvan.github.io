---
layout: post
title: Command line tools for data cleaning and analysis
---

Having been a UNIX user for a while, I've seen wonderful things built out of command line utilities, particularly one-liners in [awk](https://catonmat.net/awk-one-liners-explained-part-one) and [sed](https://catonmat.net/sed-one-liners-explained-part-one). Still, I was impressed by [Data Science at the Command Line](https://www.datascienceatthecommandline.com), which constructs entire workflows that leverage the command line's inherent pipelining potential.

While I'm familiar with many of the tools mentioned in the book (`awk`, `sed`, `tr`, `wc`, bash one-liners using conditionals), I have not heard of [Vagrant](https://www.vagrantup.com/docs/cli/) and was only vaguely aware of csvkit's [extensive capabilities](https://source.opennews.org/articles/eleven-awesome-things-you-can-do-csvkit/). I like it when tools stay true to the UNIX ethos of "do one thing, do it well"*, but it's nice to have a comprehensive toolkit for a well-defined task. Not re-inventing the wheel is a noble goal to strive for.

Increasing in complexity, the book also covers [Drake](https://github.com/Factual/drake), "GNU make for data", then onto visualization. I have to admit, I'm a little less convinced about using commandline tools to visualize data. Sure, [ImageMagick](https://imagemagick.org) is very powerful and have saved me tons of time processing images in batch mode, but calling ```tee some_exploratory_plot.png | display``` everytime seems a little tedious to me.

Finally, the author covered [Weka](https://www.cs.waikato.ac.nz/ml/weka/), a Java-based tool for clustering/regression and [BigML](https://bigml.com/) for machine-learning, sprinkling in tips for using [GNU parallel](https://www.gnu.org/software/parallel/) along the way.

### On the topic of data science tools: Pandas, ggplot, seaborn

Since I have done quite a bit of data cleaning and exploratory data analysis over the years, it's worth discussing tools Python has for these tasks. [Pandas](https://pandas.pydata.org/) is Python folks' answer to the R [Tidyverse](https://www.tidyverse.org/), in the sense that both attempt to streamline common data structures and functions for interactive data analysis. But as they say, the devil is in the details.

Where the tidyverse comes with its own visualization library, the well-known [ggplot2](https://ggplot2.tidyverse.org/) package, Python folks are blessed and cursed with options: the old-school [matplotlib](https://matplotlib.org/), the new-school [seaborn](https://seaborn.pydata.org/), the web-oriented [Bokeh](https://docs.bokeh.org/en/latest), as well as a [Python version of ggplot](http://ggplot.yhathq.com/).

Being written in 2014, `Data Science at the Command Line` undoubtedly will feel a bit limited or quaint for newer generations of data science folks. Still, it is a useful guide for people looking to expand their toolkit, and the author should be commended. As they say, the classics never die.

*_maybe I'm just old and cranky :)_
