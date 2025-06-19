---
layout: post
title: Recommender Systems
---

I enjoy movies, particularly film critique and cinematography (you should check out the excellent YouTube series [Every Frame A Painting](https://www.youtube.com/user/everyframeapainting) for some thoughtful discussions on these topics). When looking for sample data to play with recommender systems, I compiled a list of movies I have seen, and my personal 1-10 rating for them [here](https://github.com/ptvan/movies). Some common approaches to recommender systems are:

### Demographic-based Recommendation

This approach recommends movie based on demographics (age, gender, race, etc...) of the user or the user's friends. It has the benefit of not needing more detailed information from the user. But I'm not comfortable with scraping my friend's social media feeds, so won't be using it.

### Context-based Recommendation

This is where recommendations would be made based on the user's current context (eg. what webpages they view, products they buy, etc...). Sounds like it could be very accurate at least in the short term, but I also won't be using it for reasons similar to above.

### Collaborative Filtering

This is where I would look at people who like similar movies to me. The general assumption is that people who liked similar movies in the past will also like similar movies in the future. Collaborative filtering got attention in the wake of the [Netflix Prize](https://en.wikipedia.org/wiki/Netflix_Prize), where some competitors used [matrix factorization](https://en.wikipedia.org/wiki/Matrix_factorization_(recommender_systems)) on the matrix of reviews. One complication, called the "cold start" problem, is that since not everyone will have seen every movie, this matrix can be very sparse.

For my exercise, [MovieLens](https://grouplens.org/datasets/movielens/) has 2 free datasets available for public use: a more recent, frequently updated set with ~100,000 ratings and and larger archived set ~27,000,000 ratings. First, I had to clean my data a bit. Turns out, there are quite a few movies with the same titles (eg. "Richard III", or "Aladdin") but for simplicity's sake I simply [excluded them](https://github.com/ptvan/movies/blob/master/clean_movies_for_ALS.py).

Then, I ran my data through an [Alternating Least Squares](https://en.wikipedia.org/wiki/Matrix_completion#Alternating_least_squares_minimization) (ALS) function. This involved training a model on MovieLens, adding my movies, then generating [predictions](https://github.com/ptvan/movies/blob/master/spark_ALS.py). The Spark [implementation of ALS](https://spark.apache.org/docs/latest/ml-collaborative-filtering.html) allows users to deal with cold-start by either allowing NaN values for the prediction, or to drop rows containing them.

#### Some words about tools: Apache Spark

Since I'd be handling fairly large datasets, I looked into Apache [Spark](https://spark.apache.org/). Spark is written in Scala and its native API is also in Scala. Which means you're also tied to the JDK for better and worse. Most notably, Spark 2.x only runs on Java 1.8. Depending on your setup, this could be a minor inconvenience, or a better part of an afternoon hunting down unsupported community versions of the JDK and linking your tools. If you don't want to use the native Scala API there are interfaces for Python (PySpark), and R (SparkR and [SparklyR](https://spark.rstudio.com/)). I went with PySpark.

Job management is done with a web GUI (default `http://localhost:4040`), where you can view the queue of current and past jobs. Performance tuning in Spark can be a bit [more involved](https://spark.apache.org/docs/latest/tuning.html).

Spark's basic data structure is the Resilient Distributed Dataset ([RDD](https://spark.apache.org/docs/latest/rdd-programming-guide.html)). You can work with RDD directly, but for analyses it's nicer to use [Spark DataFrames](https://spark.apache.org/docs/latest/sql-programming-guide.html). Spark DataFrames have similarities with, but are **not** entirely equivalent to [Pandas dataframes](https://pandas.pydata.org/pandas-docs/stable/getting_started/dsintro.html#dataframe). For one, Spark DataFrames are immutable, since they're based on RDDs which are themselves immutable, while Pandas dataframes are mutable. If that's not enough ways to work, Spark also has an [SQL interface](https://spark.apache.org/sql/).

Spark's machine learning API is changing from `spark.mllib` (supporting RDDs) to `spark.ml` (supporting Spark DataFrames), so new code should use the latter, though apparently the former is [not deprecated](https://spark.apache.org/docs/latest/ml-guide.html#announcement-dataframe-based-api-is-primary-api). You can also plug in your favorite deep learning frameworks ([Keras](https://github.com/maxpumperla/elephas/), [DeepLearning4J](https://github.com/deeplearning4j)) to do deep learning.

### Content-based filtering

This is where I would look at find patterns in movies I like, and make recommendations based on those patterns.
Here we're recommending movies with synopses similar to the ones the user likes. The general steps are:

1. I obtained an API key from [OMDBAPI](https://www.omdbapi.com/), which allows 1000 queries/day. Until I figure out how to query multiple movies in the same request, that means a maximum 1000 movies a day.
2. Using the ~~pyCurl~~ `requests` library, I [fetched the metadata](https://github.com/ptvan/movies/blob/master/fetch_movie_metadata.py) for movies in my list, specifically full text of the synopses. (pyCurl turned out to be more powerful but much more complicated than I needed)
3. Reduced the synopsis into keywords using the Rapid Automatic Keyword Extraction ([RAKE](https://pypi.org/project/rake-nltk/)) algorithm, which is part of the Python Natural Language Toolkit ([NLTK](https://www.nltk.org/)).
4. Calculate similarity between the movies' keywords. [Cosine similarity](https://en.wikipedia.org/wiki/Cosine_similarity) is often used, but other metrics could also work.
5. Create a `recommendations()` function that gives the most similar movies (shortest cosine distance) to the one the user gives.

### Evaluating recommendations

Though accuracy is a traditional metric in recommendations, _serendipity_ or the ability of a recommendation to pleasantly surprise you, is also important, as eloquently explained in Eugene Yan's [blog post](https://eugeneyan.com/writing/serendipity-and-accuracy-in-recommender-systems/).

### References

I find [Practical Recommender Systems](https://www.manning.com/books/practical-recommender-systems) to be a good overview, going from concepts to specific implementation. As indicated by "practical" in the title, there is heavy emphasis on project work.