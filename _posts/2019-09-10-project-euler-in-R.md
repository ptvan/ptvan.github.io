---
layout: post
title: Project Euler in R
---

I thought it would be fun to test my R skills by doing [Project Euler](https://projecteuler.net/). Modern programming languages have rather full-featured libraries, but it's still nice to learn (or re-learn) things from first principles, or see what others come up with. The lessons I learned so far are:

* Project Euler is great for stretching your programming muscles. Specifically, it forces you to really understand classic/fundamental structures and algorithms (through implementing them). You also learn the strengths of the language you're using (at the cost of also exposing its weaknesses).

* Libraries are wonderful: many Project Euler problems involve handling large integers, big matrices, or dates.
It's tedious to re-invent low-level algorithms for common tasks. This point complements the point above.

* The best way to learn are to write everything 3 times: first to get it to work, second to get it to work correctly, third to get it to perform reasonably well

* Brute-force solutions have their place. Computers are fast now, and sometimes code legibility is worth the extra CPU cycles (ie. that old adage about premature optimization).

* We stand on the shoulder of giants: the body of work in math and algorithm is vast. It's fun to re-trace the steps of pioneers.

You can see the results in this GitHub repository: [euler-r](https://github.com/ptvan/euler-r).