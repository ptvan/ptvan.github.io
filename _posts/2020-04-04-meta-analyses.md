---
layout: post
title: Meta-analyses
---

Meta analyses have been around for a long time. By some accounts, the first meta-analyses trace back to 17th century astronomy research. They are also prevalent in medical research, with papers starting in 1900s. Since 1993, the [Cochrane Reviews](https://www.cochranelibrary.com/) have published comparative health findings. More recently, the growth of open data initiatives have made it easier to perform data-integration and meta analyses in your favorite languages.

### Rationale

Meta-analyses, when done properly, have both conceptual and statistical benefits. Conceptually, meta-analyses can detect the presence of publication bias. Statistically, results from individual studies can be combined to make conclusions more generalizable, and estimates can have improved precision and accuracy.

### Publication bias

Since meta-analyses use published data, a concern is [publication bias](https://en.wikipedia.org/wiki/Publication_bias). [PRISMA](http://www.prisma-statement.org/), criteria for minimum levels of evidence is used by both authors and reviewers to identifying and reducing publication bias.

### General steps of meta-analysis workflow

1. Exploratory analysis to identify data anomalies

2. Normalize the studies' reported metrics (eg. [relative risk](https://en.wikipedia.org/wiki/Relative_risk), [odds ratios](https://en.wikipedia.org/wiki/Odds_ratio))

3. Choose and fit the appropriate model(s) (eg. fixed-, random-, or mixed-effects)

4. Validate the results

### Visualization

For exploratory data analysis, a [Q-Q plot](https://en.wikipedia.org/wiki/Q%E2%80%93Q_plot) is helpful in assessing the datasets' distributions for anomalies. For comparing metrics across studies , a [forest plot](https://en.wikipedia.org/wiki/Forest_plot) (sometimes called a catepillar plot) or [funnel plot](https://en.wikipedia.org/wiki/Funnel_plot) can also be employed.

### Implementations

There are a number of R packages to perform meta-analyses, including `meta`, `rmeta`, and [`metafor`](http://www.metafor-project.org/doku.php/help). The documentation for `metafor` has a handy chart [comparing the three packages](https://cran.r-project.org/web/packages/metafor/vignettes/metafor.pdf).

`PyMeta` is an [online tool](http://www.pymeta.com/), which has an offline package called [PythonMeta](https://pypi.org/project/PythonMeta/) obtainable via pip.

### References

A basic overview of meta-analyses, including PRISMA can be found in [Haidich 2010](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3049418/). There are links to further references at this [meta_analysis_books repo](https://github.com/wviechtb/meta_analysis_books).
