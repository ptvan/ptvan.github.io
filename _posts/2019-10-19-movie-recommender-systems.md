---
layout: post
title: Recommending movies with Spark
---

I watch a lot of movies. I enjoy thinking and talking about movies (you should check out the excellent YouTube series [Every Frame A Painting](https://www.youtube.com/user/everyframeapainting)). So I compiled a list of movies I have seen, and my personal 1-10 rating for them [here](https://github.com/ptvan/movies) as an example data set for playing with recommender systems.

### Collaborative filtering

This is where I would look at people who like similar movies to me. The assumption is that people who liked similar movies in the past will also like similar movies in the future. [MovieLens](https://grouplens.org/datasets/movielens/) has 2 free datasets available for public use: a more recent, frequently updated set with ~100,000 ratings and and larger archived set ~27,000,000 ratings.

### Content-based filtering

This is where I would look at the traits of the movies I like (eg. director/writer/cinematographer, plot, country of origin, release date, etc...), find patterns, and make recommendations based on those patterns. Maybe an open version of IMDB like [OMDBAPI](https://www.omdbapi.com/) ?

### Apache Spark

For people using R and [Slurm](https://slurm.schedmd.com/overview.html) for computationally-intensive tasks, Apache [Spark](https://spark.apache.org/) feel quite different. Some things worth noting:

* Spark is written in Scala and its native API is also in Scala. Which means you're also tied to the JDK for better and worse. Most notably, the most recent version of Spark (2.4.4) only runs on Java 1.8. Depending on your setup, this could be a minor inconvenience, or a better part of an afternoon hunting down unsupported community versions of the JDK and making sure all your tools point to that. If you don't want to use Scala, there are interfaces for Python (PySpark), and R (actually multiple, SparkR and [SparklyR](https://spark.rstudio.com/)). I went with PySpark.

* Job management is a little more robust, but can also bit a bit more involved. Spark has a web GUI (default port 4040) where you can view the queue of current and past jobs.