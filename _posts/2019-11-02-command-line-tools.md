---
layout: post
title: Command line tools for data cleaning and analysis
---

Having been a UNIX user for a while, I know of the wonderful things built out of command line utilities, like one-liners in [awk](https://catonmat.net/awk-one-liners-explained-part-one), [sed](https://catonmat.net/sed-one-liners-explained-part-one), or [bash](http://www.bashoneliners.com). I also knew of Erick Matson's excellent guide to "second-generation" [shell tools](http://erick.matsen.org/2020/01/04/2nd-gen-interactive-shell.html) (`tmux`,`fd`, `ag`, etc.).

### Bioinformatics and dealing with big data

Working in bioinformatics, I have also come across a whole cottage industry of [bioinformatics oneliners](https://github.com/stephenturner/oneliners) using `bcftools` and `samtools` (and their refined variants, eg. [sambamba](https://lomereiter.github.io/sambamba/)). There are also established workflow languages to glue these tools together, as I have described in a [previous post](https://ptvan.github.io/workflow-managers/).

There are also bioinformatic variants of classic UNIX tools, like `seqtk` and `bioawk` . When dealing with big data, it's good to use parallelize, using both a general-purpose tool like [GNU Parallel](https://www.gnu.org/software/parallel/) and parallelized versions of existing tools, like [pigz](https://zlib.net/pigz/). Often, these tools are picked the hard way, as documented in this wonderfully informative blogpost about [analyzing 25TB of sequencing data](https://livefreeordichotomize.com/2019/06/04/using_awk_and_r_to_parse_25tb/).

### Data Science at the Command Line

The [Data Science at the Command Line](https://www.datascienceatthecommandline.com/) book, now in its 2nd edition, gives a pretty good big-picture view.

While I'm familiar with many of the tools the author mentions, I have not heard of [Vagrant](https://www.vagrantup.com/docs/cli/) and was only vaguely aware of csvkit's [extensive capabilities](https://source.opennews.org/articles/eleven-awesome-things-you-can-do-csvkit/). I like it when tools stay true to the UNIX ethos of "do one thing, do it well", but it's nice to have a comprehensive toolkit for a well-defined task. Not re-inventing the wheel is a noble goal to strive for.

Increasing in complexity, the book also covers [Drake](https://github.com/Factual/drake), "GNU make for data", then onto visualization. I have to admit, I'm a little less convinced about using commandline tools to visualize data. Sure, [ImageMagick](https://imagemagick.org) is very powerful and have saved me tons of time processing images in batch mode, but calling ```tee some_exploratory_plot.png | display``` everytime seems a little tedious to me.

Finally, the author covered [Weka](https://www.cs.waikato.ac.nz/ml/weka/), a Java-based tool for clustering/regression and [BigML](https://bigml.com/) for applying ML models.
