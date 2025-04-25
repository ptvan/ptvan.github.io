---
layout: post
title: Command line tools for data cleaning and analysis
---

Having been a UNIX user for a while, I know of the wonderful things built out of command line utilities, like one-liners in [awk](https://catonmat.net/awk-one-liners-explained-part-one), [sed](https://catonmat.net/sed-one-liners-explained-part-one), or even [bash](http://www.bashoneliners.com) itself. I also knew of Erick Matson's excellent guide to "second-generation" [shell tools](http://erick.matsen.org/2020/01/04/2nd-gen-interactive-shell.html) (`tmux`,`fd`, `ag`, etc.). The beauty of command line tools is you can chain them together, from the humble `cut`, `grep` to the new [verticalize](https://github.com/lindenb/verticalize), and you can wrapping your code in [expect](https://core.tcl-lang.org/expect/index) to handle interactivity.

### Processing text: CSV and JSON

Since manipulating structured text is such a common task, there are [quite a few tools available](https://github.com/dbohdan/structured-text-tools). Recently, [Miller](https://github.com/johnkerl/miller/) has gained in popularity, being able to not simply parse CSVs, but also perform SQL-like queries and joins, calculate summary statistics and perform basic regression. Miller will also handle JSONs. Though if you're working with JSONs a lot, it's probably better to use [JQ](https://stedolan.github.io/jq/) and [similar JSON utilities](https://github.com/fiatjaf/awesome-jq).

### Bioinformatics and dealing with big data

Working in bioinformatics, I have also come across a whole cottage industry of [bioinformatics oneliners](https://github.com/stephenturner/oneliners) using `bcftools` and `samtools` (and their refined variants, eg. [sambamba](https://lomereiter.github.io/sambamba/)). For FASTQ files there is the excellent [fastp](https://github.com/OpenGene/fastp). To glue these tools together, there are workflow managers as I have described in a [previous post](https://ptvan.github.io/workflow-managers/).

There are also bioinformatic variants of classic UNIX tools, like `seqtk` and `bioawk` . When dealing with big data, it's good to parallelize your tasks, using both a general-purpose tool like [GNU Parallel](https://www.gnu.org/software/parallel/) and parallelized versions of existing tools, like [pigz](https://zlib.net/pigz/) for `gzip`. Often, these tools are picked the hard way, as documented in this wonderfully informative blogpost about [analyzing 25TB of sequencing data](https://livefreeordichotomize.com/posts/2019-06-04-using-awk-and-r-to-parse-25tb/).

### Data Science at the Command Line 

The [Data Science at the Command Line](https://www.datascienceatthecommandline.com/) book gives a pretty good overview of the subject (the second edition was published in 2021).

While I'm familiar with many of the tools the author covered, at the time I have not heard of [Vagrant](https://www.vagrantup.com/docs/cli/) and was only vaguely aware of [csvkit](https://source.opennews.org/articles/eleven-awesome-things-you-can-do-csvkit/)'s extensive capabilities. I like it when tools stay true to the UNIX ethos of "do one thing, do it well", but it's nice to have a comprehensive toolkit for a narrowly-defined task. Not re-inventing the wheel is a noble goal to strive for.

Increasing in complexity, the book also covers [Drake](https://github.com/Factual/drake), "GNU make for data", then onto visualization. I have to admit, I'm a little less convinced about using command line tools to visualize data. Sure, [ImageMagick](https://imagemagick.org) is very powerful and have saved me tons of time processing images in batch mode, but calling ```tee some_exploratory_plot.png | display``` everytime seems a little tedious to me. **UPDATE: see below**

Finally, the author covered [Weka](https://www.cs.waikato.ac.nz/ml/weka/), a Java-based tool for clustering/regression and [BigML](https://bigml.com/) for applying ML models.

The second edition added more tools: [Tapkee](https://tapkee.lisitsyn.me/) for dimensional reduction, regression with [Vowpal Wabbit](https://vowpalwabbit.org/), among others. The author also contributed additional utilities in his [own GitHub Repo](https://github.com/jeroenjanssens/data-science-at-the-command-line).

### Visualizing data in the command line

Visualizing data in the command line used to mean _exporting_ your figures into JPG/PNG files, then opening them with another GUI program. However, now you can feed your CSV (or even STDIN pipes, from say, your favorite [light-weight database](https://duckdb.org)) into [YouPlot](https://github.com/red-data-tools/YouPlot) and make plots appear in the command line. 
