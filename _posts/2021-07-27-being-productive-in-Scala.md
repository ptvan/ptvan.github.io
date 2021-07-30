---
layout: post
title: Being productive in Scala
---

A long time ago, when the Earth's crust had just cooled, I learned Java. Some years later, my best friend told me about [Clojure](https://clojure.org/), a functional language that compiles to the JVM. The idea was intriguing to me, but at that point, I felt it was maybe a little niche (my friend had pitched Clojure as a language to do massively parallel simulations). Since then, other languages targeting the JVM had popped up. I re-entered the fray with Scala.

### Language features

Despite their similarities, Scala's syntax can cause some [problems for Java programmers](http://jim-mcbeath.blogspot.com/2008/09/scala-syntax-primer.html) beyond [different names for similar ideas](https://docs.scala-lang.org/tutorials/scala-for-java-programmers.html).

### Build systems

You can compile and link Scala code with [sbt](https://www.scala-sbt.org/), the predominant build tool. However, it is by no means the only option. Others include [Gradle](https://gradle.org/) and [Mill](https://www.lihaoyi.com/post/MillBetterScalaBuilds.html), the latter which created to address some of sbt's perceived shortcomings.
