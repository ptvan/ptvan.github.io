---
layout: post
title: Recommending movies, part 2 - Content-based filtering
---

See [part1](https://ptvan.github.io/movie-recommender-part1) for background information and results from collaborative filtering. Onward...

### Recommender approach 2: content-based filtering

This is where I would look at find patterns in movies I like, and make recommendations based on those patterns. 

I obtained an API key from [OMDBAPI](https://www.omdbapi.com/) and fetched the synopses for my favorite movies using the ~~pyCurl~~ `requests` library (pyCurl turned out to be more powerful but much more complicated than I needed).

### Some words about tools: Pandas, ggplot, seaborn



