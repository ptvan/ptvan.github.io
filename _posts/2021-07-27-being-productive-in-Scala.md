---
layout: post
title: Being productive in Scala
---

A long time ago, when the Earth's crust had just cooled, I learned Java. Some years later, my best friend told me about [Clojure](https://clojure.org/), a functional language that compiles to the JVM. The idea was intriguing to me, but at that point, I felt Clojure was maybe a little niche (my friend had pitched Clojure as a language to do massively parallel simulations). Since then, other languages targeting the JVM had popped up. I re-entered the fray with Scala while playing with [Spark](https://ptvan.github.io/recommender-systems), and am aware of at least one group that uses [Scala on a regular basis](https://github.com/fulcrumgenomics/fgbio).

### Language features

Scala is an object-oriented programming language due to objects being first-class entities, _ie._ everything is an object. Scala is also a functional programming language, with emphasis on recursion, minimizing side-effects and being able to pass functions as arguments.

Despite their similarities, Scala's syntax can trip up [Java programmers](https://docs.scala-lang.org/tutorials/scala-for-java-programmers.html) since some common things in Java (_static_ keyword, _break_ statements, etc. ) [do not exist in Scala](http://jim-mcbeath.blogspot.com/2008/09/scala-syntax-primer.html) and other things are subtly different (infix statements).

### Building Scala code

You can compile and link Scala code with [sbt](https://www.scala-sbt.org/), the predominant build tool. However, it is by no means the only option. Others include [Gradle](https://gradle.org/) and [Mill](https://www.lihaoyi.com/post/MillBetterScalaBuilds.html), the latter which created to address some of sbt's perceived shortcomings.

The actual building process is streamlined using modern IDEs, most notably [IntelliJ](https://www.jetbrains.com/idea/), which was designed for JVM-targeting languages, but also VSCode (using its [Metals extension](https://scalameta.org/metals/docs/editors/vscode/)).

Regardless of the build system you choose, you will have to do some setup to get your Scala code to compile. You can call sbt/Mill manually, or have them watch source files to automatically recompile when there are changes.

If you instead would like to code and run a small project as quickly as possible, [Ammonite](https://ammonite.io/) turns your Scala files into self-contained executable scripts by compiling transparently behind the scene. Ammonite also adds some features to the Scala REPL.
