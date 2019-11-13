---
layout: post
title: Designing Data-Intensive Applications
---

I've run across Martin Kleppman's [Designing Data-Intensive Applications](https://dataintensive.net/) book before, and it piqued my interest. A few weeks ago a colleague mentioned it again in passing, so I thought it was time to finally read it. Below are my thoughts, added as I work my way through the book:

### Chapter 1

1. Handling faults vs. avoiding them: ~1 harddrive goes bad every day in a 10,000-drive data center. Deliberately introduce faults into systems to test resilience: NetFlix's [Chaos Monkey](https://github.com/Netflix/chaosmonkey) 

2. Differing system loads: Posting a tweet (low load) vs. viewing Twitter home timeline (high load). Two different approaches: keeping a global collection of tweets vs. maintaining each user's collection of tweets and retweets. Implementation varies by type of user: high-intensity users (ie. celebrities) served by first approach, regular users served by second

3. Latency vs. response: latency is duration a request is waiting to be served, response is what the user sees
