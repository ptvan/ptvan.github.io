---
layout: post
title: Statistical literacy
---

Whether we like it or not, we encounter a lot of claims during the course of everyday life. These claims range from the relatively trivial ("the best comedy series on television right now !") to the deeply significant with wide-ranging impacts ("drug X is better for this disease than drug Y"). Though my work often exposes me to the latter, I think everyone can benefit from statistical understanding, in particular what these claims mean, how they are backed up by evidence, and being able to spot bad reasoning where they occur.

### Extraordinary claims require extraordinary evidence

I first encountered this saying in an undergraduate class, where it was said during a lecture (I forgot the broader context, unfortunately) It stuck with me because it is both a truth and a warning. Less dramatically, I think it's important to maintain a health skepticism of dramatic claims. A side note, speaking of the dramatic, the classic "How to Lie With Statistics" book turns out to have a [complicated legacy](https://www.refsmmat.com/articles/smoking-statistics.html).

We often hear on the news that "new studies discover a link between [a disease] and [an activity or food]". This news rarely goes into the _sample size_ and _effect size_ of the studies. Early studies that show effect are often invalidated by larger later follow-up studies. This does not mean that the science is suspect. Science is informed by evidence, and when the evidence is incomplete or misunderstood, science suffers. But it also means additional data can drastically improve our understanding by clearing up past misconceptions.

### Common statistical problems and fallacies

**P-values**: Despite its widespread use, P-values are often misunderstood. Probably the most common misconception is that p-values do not make guarantees about the null hypothesis, nor does it necessarily support the alternative hypothesis. A statistically significant p-value also does not mean that a _practically significant_ effect has been found. When many hypothesis tests are performed, such as in the case of microarray or NGS data, P-values can also be inflated, requiring _multiple comparison correction_.

**Statistical independence**: Many statistical tests and models assume that the observations are independent, though in practice this assumption is sometimes violated. For example, weight and height are often correlated in biological data: a large mouse is usually also heavy.

**Pseudoreplication**: I previously talked about pseudoreplication in [my post on experimental design](https://ptvan.github.io/experimental-design/). This occurs when the experiment does not have enough replication, or the replications are not statistically independent.

**Base-rate fallacy**: also called _false positive paradox_, this occurs when we ignore the general prevalence of a event, also called the _base rate_ of a test.

**Simpson's paradox**: this occurs when trends observed in different parts of a dataset reverses when these parts are combined into a single dataset. Usually this happens when a confounding variable is involved but hasn't been accounted for.

**Berkson's paradox**: also called _collider bias_, this occurs when two independent events appear to be correlated in a dataset.

### Further reading

Carl Bergstrom's [Calling Bullshit](https://callingbullshit.org/) covers some of this blogpost's points. Begun as a book, Bergstrom's efforts (working with colleague Jevin West) more recently include [Bullshit Machines](https://thebullshitmachines.com/) concerning LLMs. Other books on statistical literacy include 
[The Tiger That Isn't](https://plus.maths.org/content/tiger-isnt) and [The Art of Statistics](https://medium.com/@juntaah/review-the-art-of-statistics-david-spiegelhalter-ed366f4102ea). I haven't read these latter two (the links are to reviews), but intend to in the future.

Emily Oster documents several instances where health recommendations given to pregnant women were based on historical studies with small and/or unrepresentative samples in her book [Expecting Better](https://www.penguinrandomhouse.com/books/310896/expecting-better-by-emily-oster/).

Steven Goodmans' ["Twelve p-value misconceptions"](https://pubmed.ncbi.nlm.nih.gov/18582619/) is a good summary of the subject. The original is unfortunately locked behind a paywall, though you can find some of the same contents elsewhere, I find [this article](https://daniellakens.blogspot.com/2017/12/understanding-common-misconceptions.html) particularly useful due to its inclusion of plots showing the distributions. For multiple comparison correction, there is helpful coverage in [John McDonald's LibreTexts book](https://stats.libretexts.org/Bookshelves/Applied_Statistics/Biological_Statistics_(McDonald)/06%3A_Multiple_Tests/6.01%3A_Multiple_Comparisons).

Berkson's paradox was recently illustrated using [real-world COVID data](https://pmc.ncbi.nlm.nih.gov/articles/PMC10016947/).
