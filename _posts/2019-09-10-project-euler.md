---
layout: post
title: Project Euler in R and Python
---

I thought it would be fun to test my R skills by doing [Project Euler](https://projecteuler.net/). Modern programming languages have rather full-featured libraries, but it's still nice to learn (or re-learn) things from first principles, or see what others come up with. You can see the results in this GitHub repository: [euler-r](https://github.com/ptvan/euler-r).

The lessons I learned so far are:

* Project Euler is great for stretching your programming muscles. Specifically, it forces you to really understand classic/fundamental structures and algorithms (through implementing them). You also learn the strengths of the language you're using (at the cost of also exposing its weaknesses).

* Libraries are wonderful: many Project Euler problems involve handling large integers, big matrices, or dates. It's tedious to re-invent low-level algorithms for common tasks. This point complements the point above.

* A good way to learn is to write everything 3 times: first to write code that works, second to get it to work correctly, third to get it to perform reasonably well.

* Brute-force solutions have their place. Computers are fast now, and sometimes code legibility is worth the extra CPU cycles (ie. that old adage about premature optimization).

* On the other hand, since many Project Euler problems are rooted in math, there exist elegant (or at least more efficient) solutions if you're familiar with, for example, [binomial theorem](https://en.wikipedia.org/wiki/Binomial_theorem) or the properties of [prime numbers](https://en.wikipedia.org/wiki/Prime_number#Analytic_properties). This leads me to my next point:

* We stand on the shoulder of giants: the body of knowledge in math and algorithms is vast. It's fun to re-trace the steps of pioneers.

After doing a few problems in R, I reimplimented them in [Python](https://github.com/ptvan/euler-python). I'm enjoying seeing the subtle (and not so subtle) ways the two languages differ. I like R but found its [TIMTOWTDI](https://en.wikipedia.org/wiki/There%27s_more_than_one_way_to_do_it) approach to be bewildering at times (eg. do we really need [3 different object systems](http://adv-r.had.co.nz/OO-essentials.html) ?). Lessons learned for Python so far:

* [List comprehensions](https://docs.python.org/3/tutorial/datastructures.html#list-comprehensions) are nice syntactic sugar.

* The [with](https://docs.python.org/2.5/whatsnew/pep-343.html) statement is nice, especially in long pipelines where you otherwise would have to do a lot of cleaning up.

* As was the case in R, it's good to be familiar with your libraries. For project Euler in particular, [math](https://pypi.org/project/maths/) is very helpful.
