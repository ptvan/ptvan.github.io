---
layout: post
title: Data stores
---

As emphasized by people [more knowledgable than me](https://ptvan.github.io/Designing-DataIntensive-Applications/), picking the right data store is important when you have a lot of data, need to access it frequently, or are working with it intensely. In this post I've compiled some notes as I worked with different data stores.

### SQL
More scalable than storing your data in a bunch of flat files or [SQLite](https://www.sqlite.org/index.html), RBDSMs are probably most straightforward data store: data is tabular, queried via some variant of SQL and stored on a single server (though some offer clustering/sharding). MySQL/[MariaDB](https://mariadb.org/), [PostgreSQL](https://www.postgresql.org/) and [SQLServer](https://www.microsoft.com/en-us/sql-server/default.aspx) are all established, well-regarded solutions.  

### Cassandra

### MongoDB

### Neo4J
