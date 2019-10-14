---
layout: post
title: Project Euler in Python
---

Now that I've done a few Project Euler problems in R, it's time to reimpliment them in [Python](https://github.com/ptvan/euler-python). I'm enjoying seeing the subtle (and not so subtle) ways the two languages differ. I like R but found its [TIMTOWTDI](https://en.wikipedia.org/wiki/There%27s_more_than_one_way_to_do_it) approach to be bewildering at times (eg. do we really need [3 different object systems](http://adv-r.had.co.nz/OO-essentials.html) ?). Lessons learned for Python so far:

* [List comprehensions](https://docs.python.org/3/tutorial/datastructures.html#list-comprehensions) are nice syntactic sugar.
 
* The [with](https://docs.python.org/2.5/whatsnew/pep-343.html) statement is nice, especially in long pipelines where you otherwise
would have to do a lot of cleaning up.

* As was the case in R, it's good to be familiar with your libraries. For project Euler in particular, [math](https://pypi.org/project/maths/) is very helpful.
