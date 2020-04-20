---
layout: post
title: Meta-analyses
---

Meta analyses have been around for a long time. By some accounts, the first meta-analyses trace back to 17th century astronomy research. They are also prevalent in medical research, with papers starting in 1900s. Since 1993, the [Cochrane Reviews](https://www.cochranelibrary.com/) have published comparative health findings. More recently, the growth of open data initiatives have made it easier to perform data-integration and meta analyses in your favorite languages.

### Rationale

Meta-analyses, when done properly, have both conceptual and statistical benefits. Conceptually, meta-analyses can detect the presence of publication bias. Statistically, results from individual studies can be combined to make conclusions more generalizable, and estimates can have improved precision and accuracy.

### Visualization

For exploratory data analysis, a [Q-Q plot](https://en.wikipedia.org/wiki/Q%E2%80%93Q_plot) is helpful in assessing the datasets' distributions for anomalies. For comparing metrics across studies (eg. accuracy, sensitivity, [odds ratios](https://en.wikipedia.org/wiki/Odds_ratio)), a [forest plot](https://en.wikipedia.org/wiki/Forest_plot) (sometimes called a catepillar plot) or [funnel plot](https://en.wikipedia.org/wiki/Funnel_plot) can also be employed.

### Meta-analyses in R

The `metafor` package is well-known and [well-documented](http://www.metafor-project.org/doku.php/help). It supports fixed-, random-, and mixed-effects models, and also implements many of the visualizations above. Other packages include `meta` and `rmeta`.

### Meta-analyses in Python

`PyMeta` is an [online tool](http://www.pymeta.com/), which has a pip package counterpart called [PythonMeta](https://pypi.org/project/PythonMeta/).
