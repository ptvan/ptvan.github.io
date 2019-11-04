---
layout: post
title: Recommending movies, part 2 - Content-based filtering
---

See [part1](https://ptvan.github.io/movie-recommender-part1) for background information and results from collaborative filtering. Onward...

I obtained an API key from [OMDBAPI](https://www.omdbapi.com/) and fetched the synopses for my favorite movies using the ~~pyCurl~~ `requests` library (pyCurl turned out to be more powerful but much more complicated than I needed).

### Some words about tools: Pandas, ggplot, seaborn

Since I'll be doing a lot of exploratory data analysis and visualization, it's good to go over tools for doing these in Python. [Pandas](https://pandas.pydata.org/) is Python folks' answer to the R [Tidyverse](https://www.tidyverse.org/), in the sense that both attempt to unify and streamline common analysis and visualization tasks. But as they say, the devil is in the details.

Where the tidyverse comes with its own visualization library, the well-known [ggplot2](https://ggplot2.tidyverse.org/) package, Python folks are blessed and cursed with options: the old-school [matplotlib](https://matplotlib.org/), the new-school [seaborn](https://seaborn.pydata.org/), the web-oriented [Bokeh](https://docs.bokeh.org/en/latest), as well as a [Python version of ggplot](http://ggplot.yhathq.com/).



