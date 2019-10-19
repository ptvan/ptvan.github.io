---
layout: post
title: Movie recommender systems
---

I watch a lot of movies. I enjoy thinking and talking about movies (you should check out the excellent YouTube series [Every Frame A Painting](https://www.youtube.com/user/everyframeapainting)). So I compiled a list of movies I have seen, and my personal 1-10 rating for them [here](https://github.com/ptvan/movies) as an example data set for playing with recommender systems.

### Collaborative filtering

This is where I would look at people who like similar movies to me. I will need a database of people's ratings of movies. Perhaps [MovieLens](https://grouplens.org/datasets/movielens/)?

### Content-based filtering

This is where I would look at the traits of the movies I like (eg. director/writer/cinematographer, plot, country of origin, release date, etc...), find patterns, and make recommendations based on those patterns. Maybe an open version of IMDB like [OMDBAPI](https://www.omdbapi.com/) ?
