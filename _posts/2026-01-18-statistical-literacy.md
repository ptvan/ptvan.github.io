---
layout: post
title: Statistical literacy
---

Whether we like it or not, we encounter a lot of claims during the course of everyday life. These claims range from the trivial ("this is the best comedy series on television right now !") to the deeply significant with wide-ranging impacts ("drug X is better for this disease than drug Y"). Though my work often exposes me to the latter, I think everyone can benefit from statistical literacy: what these claims mean, how they are backed up by evidence, and being able to identify problems with them.

### Extraordinary claims require extraordinary evidence

I first encountered this saying in an undergraduate class, where it was said during a lecture (I forgot the broader context, unfortunately). It stuck with me because it is both a truth and a warning. Less dramatically, I think it's important to maintain a healthy skepticism of dramatic claims. A side note, speaking of the dramatic, the classic "How to Lie With Statistics" book turns out to have a [complicated legacy](https://www.refsmmat.com/articles/smoking-statistics.html).

### The tools of statistical literacy

Having good statistical literacy begins with a healthy skepticism of claims we encounter. We often hear on the news that "new studies discover a link between [a disease] and [an activity or food]", implying that performing the activity or consuming the food will protect us against that disease. A good first step
in evaluating claims is to rule out _spurious associations_. It's easy to laugh at [the lack of pirates is causing global warming](https://www.forbes.com/sites/erikaandersen/2012/03/23/true-fact-the-lack-of-pirates-is-causing-global-warming/), but other associations are more subtle. A more serious example might be high ice cream sales is correlated with drowning in swimming pools. Both ice cream sales and pool usage (and thus, drownings) are confounded by seasonality, summer being a time when people increase both swimming and ice cream consumption.

Returning to media coverage of new discoveries, these announcements rarely mention the _sample size_ or _effect size_ of the studies, and even more rarely do they cover the experimental design. Science generally develops slowly, and engineering is bound by physics, and while there are of course exceptions, dramatic discoveries or breakthroughs are rare.  Early studies that show positive results on drug X vs. drug Y may actually only have small percentage gain that is often invalidated by larger later follow-up experiments. This does not mean that the science is suspect. Science is informed by evidence, and when the evidence is incomplete or misunderstood, science suffers. Even more subjective claims like "best comedy series on television" falls apart under scrutiny: this result may have determined by polling a handful of audience members who already like comedies more than the average watcher. Observational, especially self-reported data is often less reliable, not because of malice, but because humans are subject to many [cognitive biases](https://en.wikipedia.org/wiki/List_of_cognitive_biases).

Further developing statistical literacy requires understanding fundamental concepts like representative samples and confounders, what hypothesis testing requires and assumes, fluency in reading graphics, _etc_. It also requires more general scientific skills like experiment design and specific practical skills like making clear graphics and visualizations that do not mislead.

### Common statistical problems and fallacies

**Statistical independence**: Many statistical tests and models assume that the observations in the data are independent, though in practice this assumption is sometimes violated. For example, weight and height are often correlated in biological data: a large mouse is usually also heavy so these two variables cannot be treated as independent.

**Visually misleading graphics**: this is a large category of problems including truncating axes or displaying quantities as volumes instead of lines which makes differences appear larger, improperly binning or omitting values which distorts the signficance of trends.

**Pseudoreplication**: I previously talked about pseudoreplication in [my post on experimental design](https://ptvan.github.io/experimental-design/). This occurs when the experiment does not have adequate replication, or the replications are not statistically independent.

**Base-rate fallacy**: also called _false positive paradox_, this occurs when we ignore the general prevalence of a event, also called the _base rate_ of a statistical test.

**Simpson's paradox**: this occurs when trends observed in different parts of a dataset reverses when these parts are combined into a single dataset. Usually this happens when a confounding variable is present in the data but hasn't been accounted for.

**Berkson's paradox**: also called _collider bias_ and closely related to Simpson's paradox, this occurs when two independent events appear to be correlated in a dataset.

**P-values**: Despite their widespread use, P-values are often misunderstood. P-values do not make guarantees about the null hypothesis, nor does it necessarily support the alternative hypothesis. A statistically significant p-value also does not mean that a _practically significant_ effect has been found. When many hypothesis tests are performed, such as in the case of microarray or NGS data, P-values can also be inflated, requiring _multiple comparison correction_.

### Further reading

Carl Bergstrom's [Calling Bullshit](https://callingbullshit.org/) covers some of this blogpost's points. In addition, Bergstrom's efforts (working with colleague Jevin West) more recently include [Bullshit Machines](https://thebullshitmachines.com/) concerning LLMs. Other books on statistical literacy include [The Tiger That Isn't](https://plus.maths.org/content/tiger-isnt) and [The Art of Statistics](https://medium.com/@juntaah/review-the-art-of-statistics-david-spiegelhalter-ed366f4102ea). I haven't read these two books (the links are to reviews), but intend to in the future.

Some examples of misleading graphics can be seen in this [Graph Gone Wrong article](https://medium.com/@Ana_kin/graphs-gone-wrong-misleading-data-visualizations-d4805d1c4700).

Emily Oster documents several instances where health recommendations given to pregnant women were based on historical studies with small and/or unrepresentative samples in her book [Expecting Better](https://www.penguinrandomhouse.com/books/310896/expecting-better-by-emily-oster/).

Edward Tufte has a well-regarded series of [books on statistical graphics](https://www.edwardtufte.com/books/) starting with the classic "The Visual Display of Quantitative Information" which discusses some visually misleading graphics.

Berkson's paradox was recently illustrated using [real-world COVID data](https://pmc.ncbi.nlm.nih.gov/articles/PMC10016947/).

Steven Goodmans' ["Twelve p-value misconceptions"](https://pubmed.ncbi.nlm.nih.gov/18582619/) is a good summary of the subject. The original is unfortunately locked behind a paywall, though you can find some of the same contents elsewhere, I find [this article](https://daniellakens.blogspot.com/2017/12/understanding-common-misconceptions.html) particularly useful due to its inclusion of plots showing the distributions. For multiple comparison correction, there is helpful coverage in [John McDonald's Biological Statistics](https://stats.libretexts.org/Bookshelves/Applied_Statistics/Biological_Statistics_(McDonald)/06%3A_Multiple_Tests/6.01%3A_Multiple_Comparisons).
