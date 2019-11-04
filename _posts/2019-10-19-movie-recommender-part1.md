---
layout: post
title: Recommending movies, part 1 - Collaborative Filtering with Spark
---

I like filmmaking, particularly cinematography (you should check out the excellent YouTube series [Every Frame A Painting](https://www.youtube.com/user/everyframeapainting) for some thoughtful discussions on these topics). When looking for sample data to play with recommender systems, I compiled a list of movies I have seen, and my personal 1-10 rating for them [here](https://github.com/ptvan/movies). Two common approaches to recommender systems are:

### Recommender approach 1: collaborative filtering

This is where I would look at people who like similar movies to me. The assumption is that people who liked similar movies in the past will also like similar movies in the future. [MovieLens](https://grouplens.org/datasets/movielens/) has 2 free datasets available for public use: a more recent, frequently updated set with ~100,000 ratings and and larger archived set ~27,000,000 ratings.

First, I had to clean my data a bit. Turns out, there are quite a few movies with the same titles (eg. "Richard III", or "Aladdin") but for simplicity's sake I simply [excluded them](https://github.com/ptvan/movies/blob/master/clean_movies_for_ALS.py).

Then, I ran my data through an [Alternating Least Squares](https://en.wikipedia.org/wiki/Matrix_completion#Alternating_least_squares_minimization) (ALS) function. This involved training a model on MovieLens, adding my movies, then generating [predictions](https://github.com/ptvan/movies/blob/master/spark_ALS.py).

### Some words about tools: Apache Spark

Since I'd be handling fairly large datasets, Apache Spark was worth looking into. For people used to [R](https://r-project.org) and [Slurm](https://slurm.schedmd.com/overview.html) for computationally-intensive tasks, a workflow based on Apache [Spark](https://spark.apache.org/) feels quite different. Some things worth noting:

* Spark is written in Scala and its native API is also in Scala. Which means you're also tied to the JDK for better and worse. Most notably, Spark 2.x only runs on Java 1.8. Depending on your setup, this could be a minor inconvenience, or a better part of an afternoon hunting down unsupported community versions of the JDK and making sure all your tools point to that. If you don't want to use Scala, there are interfaces for Python (PySpark), and R (actually multiple, SparkR and [SparklyR](https://spark.rstudio.com/)). I went with PySpark.

* Job management is a little more accessible in Spark, with a web GUI (default `http://localhost:4040`), where you can view the queue of current and past jobs. Performance tuning in Spark can be a bit [more involved](https://spark.apache.org/docs/latest/tuning.html). 

* Spark's basic data structure is the Resilient Distributed Dataset ([RDD](https://spark.apache.org/docs/latest/rdd-programming-guide.html)). You can work with RDD directly, but for analyses it's nicer to use [Spark DataFrames](https://spark.apache.org/docs/latest/sql-programming-guide.html). Spark DataFrames have similarities with, but are not entirely equivalent to [Pandas dataframes](https://pandas.pydata.org/pandas-docs/stable/getting_started/dsintro.html#dataframe). For one, Spark DataFrames are immutable, since they're based on RDDs, which are themselves immutable, while Pandas dataframes are mutable. If that's not enough ways to work, Spark also has an [SQL interface](https://spark.apache.org/sql/). 

* Spark's machine learning API is changing from `spark.mllib` (supporting RDDs) to `spark.ml` (supporting Spark DataFrames), so new code should use the latter, though apparently the former is [not deprecated](https://spark.apache.org/docs/latest/ml-guide.html#announcement-dataframe-based-api-is-primary-api). You can also plug in your favorite deep learning frameworks ([Keras](http://maxpumperla.com/elephas/), [DeepLearning4J](https://deeplearning4j.org/docs/latest/deeplearning4j-scaleout-intro)) to do deep learning.


### Recommender approach 2: content-based filtering

This is where I would look at find patterns in movies I like, and make recommendations based on those patterns. This is the subject of [another post](https://ptvan.github.io/movie-recommender-part2).

