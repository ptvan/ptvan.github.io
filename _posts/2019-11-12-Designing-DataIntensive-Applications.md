---
layout: post
title: Designing Data-Intensive Applications book
---

I've run across Martin Kleppman's [Designing Data-Intensive Applications](https://dataintensive.net/) book before, and it sounded interesting. A few weeks ago a colleague mentioned it again in passing, so I thought it was time to finally read it. Below are my notes, added as I work my way through the book:

### Chapter 1: Introduction

1. Handling faults vs. avoiding them: ~1 harddrive goes bad every day in a 10,000-drive data center. Deliberately introduce faults into systems to test resilience: NetFlix's [Chaos Monkey](https://github.com/Netflix/chaosmonkey).  

2. Differing system loads: Posting a tweet (low load) vs. viewing Twitter home timeline (high load). Two different approaches: keeping a global collection of tweets vs. maintaining each user's collection of tweets and retweets. Implementation varies by type of user: high-intensity users (ie. celebrities) served by first approach, regular users served by second.

3. Latency vs. response: latency is duration a request is waiting to be served, response is what the user sees.

### Chapter 2: Data Models

1. For data with many-to-many relationships, document model is better than relational model. Interestingly, document models apparently go way back to CODASYL in the 1970's.

2. Cost of schema changes must be incorporated into architecture planning, as they can be very expensive, requiring the entire table to be rewritten in the extreme case.

3. Modern RDBMS's support XML, which has some features of document models.

4. Querying using MapReduce can be more powerful but more complicated, as you have to write two separate coordinated queries for one operation.

5. An overview of graph databases and their query languages: [Cypher](https://neo4j.com/developer/cypher-query-language/), [SPARQ](https://www.w3.org/TR/rdf-sparql-query/) and [Datalog](https://clojure.github.io/clojure-contrib/doc/datalog.html).  

### Chapter 3: Storage and Retrieval

1. The hash-map is the simplest data index, easiest to implement. If kept to append-only, hash-map indices can be very fast, concurrency is simple, especially if only one writer thread is allowed. Limitations are memory sizes if implemented in memory, range queries are not efficient.

2. By contrast, SSTable (Sorted String Table) allows for larger-than-memory merging. Since they're sorted, finding a particular key is also faster.

3. LSM (Log-Structured Merge) trees are faster for write, B-trees are faster for reads.

4. "Fact tables" represent events (eg. each row in a fact table is a sale). "Dimension tables", linked to the fact table via foreign keys, represent who/what/where/why/how of that event (eg. detailed product descriptions, where the product was shipped to/from, discounts in prices). This forms a "star schema" with the fact table at the center and dimension tables as points of the star. A variation of star schema is snowflake schema, where data in dimension tables are further broken down (eg. dim_product could contain product brand and category as foreign keys), but simple star schema is simpler for analytics.

5. In real world applications, fact tables can have hundreds of columns, with analytics often only needing to query a few among them. Column-oriented stoage where columns store single bits (column bitmasking) can provide significant performance improvements since bitwise operations are very fast.

### Chapter 4: Encoding and Evolution

1. Avoid language-specific data encodings, such as Ruby's [Marshal](https://ruby-doc.org/core-2.6.3/Marshal.html), Python's [Pickle](https://docs.python.org/3/library/pickle.html) and Java's [Kryo](https://github.com/EsotericSoftware/kryo). Using these means you're tied to a particular language, and opening new attack surfaces (since restoring the data requires instantiate arbitrary classes). They're also likely not optimized.

2. XML, JSON, and CSV also have some shortcomings: encoding of numbers is ambiguous, and encoding binary data using base64 is inefficient. Furthermore, CSV doesn't support schemas, and is extra ambiguous (eg. if data contains commas/semicolons normally used as terminators)

3. Apache [Thrift](https://thrift.apache.org/) and [Protocol Buffers](https://protobuf.dev/) are binary encoding libraries that require schemas. Both, use field tags, essentially aliases for fields. Thrift has two different protocols: BinaryProtocol and CompactProtocol, the latter packs field type and tag number into a single byte to be efficient. Apache [Avro](https://avro.apache.org/), originally a subproject of Hadoop, is another binary encoding library that that obtains additional efficiency by not having field tags at all.

4. In general, new schema versions means adding field tags while leaving existing field tags to preserve compatibility, with field tags either marked as required or optional.

5. When working with data across machines (ie. web services), there are two major approaches: [REST](https://en.wikipedia.org/wiki/Representational_state_transfer) and [SOAP](https://en.wikipedia.org/wiki/SOAP). REST is tightly coupled with HTTP, using it for caching, authentication, content-type negotiation and URLs for locating resources. By contrast, while SOAP is used over HTTP, it implements a variety of different HTTP-independent standards using XML.

6. Remote Procedure Calls (RPC) has several implementations: as a built-in feature of Avro, JSON over HTTP ([Rest.li](https://linkedin.github.io/rest.li/)), Protocol Buffer's [gRPC](https://grpc.io/). Some of these frameworks provide service discovery, announcing where a client can find a particular service. Still, RPC has some shortcomings . First, rather than returning values, RPC could fail because of network interruption. Second, a network request is much slower than disk I/O. Third, calling complex functions with pointers gets costly over the network. Lastly, the client and the server could be running different languages, requiring overhead in translation.

7. Large projects can make use of message brokers like [RabbitMQ](https://www.rabbitmq.com) and Apache [Kafka](https://kafka.apache.org/).

### Chapter 5: Replication

1. There are 3 major modes of replicating data between different nodes: _leaderless_, _single-leader_ and _multi-leader_. Furthermore, the replication can also be either _synchronous_ or _asynchronous_. Synchronous replication has the benefit of being sure that the data is always up-to-date, but if there is a break in communication, the write is not processed. As a result, typical setups will implement a compromise of having one synchronous follower and the rest being asynchronous. Replication can be statement-, row- or trigger-based.

2. Multi-leader replication provides the largest scale of replication (_ie._ across data centers) but when they are retrofitted to existing systems there are be subtle pitfalls and should only be used as last resort. Some examples of multi-leader implementations are: [Tungsten Replicator](https://www.continuent.com/solutions) (mySQL/mariaDB), [BDR](https://www.2ndquadrant.com/en/resources-old/postgres-bdr-2ndquadrant/) (PostgresSQL) and [GoldenGate](https://www.oracle.com/integration/goldengate/)(Oracle).

3. In leaderless replication, clients send writes and reads to several nodes in parallel in order to ensure all nodes have most up-to-date data.

4. Resolving conflicting changes can be performed either _on-write_ or _on-read_. Some strategies for resolving conflicting changes are: giving writes unique IDs, giving replicas unique IDs, merging changes, or prompting user to perform the resolution.

### Chapter 6: Partitioning

1. Partitioning, breaking data up into _partitions_ is called different things in different implementations: _shards_, _regions_, _tablets_, _vnodes_ and _vBuckets_ .

2. Data should be allocated evenly across partitions, avoiding _skew_.

3. Partitioning can done by keys, or _hashes of keys_.

4. Skewed data needs to be _rebalanced_ to avoid _hotspots_, where processing takes more time
