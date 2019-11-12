---
layout: post
title: Recommending movies, part 2 - Content-based Filtering
---

See [part 1](https://ptvan.github.io/movie-recommender-part1) for background information and results from collaborative filtering. Onward...

### Content-based filtering using movie synopsis

Here we're recommending movies with synopses similar to the ones the user likes. The general steps are:

1. I obtained an API key from [OMDBAPI](https://www.omdbapi.com/), which lets me perform up to 1000 queries/day.
2. Using the ~~pyCurl~~ `requests` library, I [fetched the metadata](https://github.com/ptvan/movies/blob/master/fetch_movie_metadata.py) for the movies in my list. Specifically, I got the movies' synopses. (pyCurl turned out to be more powerful but much more complicated than I needed)
3. Reduced the synopsis into keywords using the Rapid Automatic Keyword Extraction ([RAKE](https://pypi.org/project/rake-nltk/)) algorithm, which is part of the Python Natural Language Toolkit ([NLTK](https://www.nltk.org/)).
4. Calculate [similarity](https://en.wikipedia.org/wiki/Cosine_similarity) between the movies' keywords.
5. Create a `recommendations()` function that gives the most similar movies to the one the user gives.