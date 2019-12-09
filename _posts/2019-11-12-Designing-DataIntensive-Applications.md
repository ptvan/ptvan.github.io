---
layout: post
title: Designing Data-Intensive Applications
---

I've run across Martin Kleppman's [Designing Data-Intensive Applications](https://dataintensive.net/) book before, and it piqued my interest. A few weeks ago a colleague mentioned it again in passing, so I thought it was time to finally read it. Below are my thoughts, added as I work my way through the book:

### Chapter 1

1. Handling faults vs. avoiding them: ~1 harddrive goes bad every day in a 10,000-drive data center. Deliberately introduce faults into systems to test resilience: NetFlix's [Chaos Monkey](https://github.com/Netflix/chaosmonkey).  

2. Differing system loads: Posting a tweet (low load) vs. viewing Twitter home timeline (high load). Two different approaches: keeping a global collection of tweets vs. maintaining each user's collection of tweets and retweets. Implementation varies by type of user: high-intensity users (ie. celebrities) served by first approach, regular users served by second.

3. Latency vs. response: latency is duration a request is waiting to be served, response is what the user sees.

### Chapter 2

1. For data with many-to-many relationships, document model is better than relational model. Interestingly, document models apparently go way back to CODASYL in the 1970's.

2. Cost of schema changes must be incorporated into architecture planning, as they can be very expensive, requiring the entire table to be rewritten in the extreme case.

3. Modern RDBMS's support XML, which has some features of document models.

4. Querying using MapReduce can be more powerful but more complicated, as you have to write two separate coordinated queries for one operation.

5. An overview of graph databases and their query languages: [Cypher](https://neo4j.com/developer/cypher-query-language/), [SPARQ](https://www.w3.org/TR/rdf-sparql-query/) and [Datalog](https://clojure.github.io/clojure-contrib/doc/datalog.html).  

### Chapter 3

1. The hash-map is the simplest data index, easiest to implement. If kept to append-only, hash-map indices can be very fast, concurrency is simple, especially if only one writer thread is allowed. Limitations are memory sizes if implemented in memory, range queries are not efficient.
