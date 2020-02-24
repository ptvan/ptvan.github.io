---
layout: post
title: Neural network noodling
---

One lesson I took away from my time in graduate school was the importance of understanding things from first principles. So for learning about neural networks, I really enjoyed reading [Grokking Deep Learning](https://www.manning.com/books/grokking-deep-learning), which implements neural networks using only `numpy`, keeping the reader from being bogged down with implementation details. Another excellent introduction is [this video](https://www.manning.com/livevideo/3blue1brown-neural-networks) video from Grant Sanderson*. If you prefer to read rather than watch, Michael Nielsen's [Neural Networks and Deep Learning](http://neuralnetworksanddeeplearning.com/) is also great.

For more details, particularly multi-layer perceptrons, I've referenced [Neural Smithing](https://mitpress.mit.edu/books/neural-smithing).

### Network tuning

One of the interesting and frustrating problems in modeling complex data is overfitting. The solution often involves a combination of picking the right tools, then knowing how to interpret their output. In a neural network context once you've picked the appropriate [architecture](https://towardsdatascience.com/the-mostly-complete-chart-of-neural-networks-explained-3fb6f2367464), the right [activation functions](https://missinglink.ai/guides/neural-network-concepts/7-types-neural-network-activation-functions-right/), you may need to implement [dropout](http://jmlr.org/papers/v15/srivastava14a.html).

*_Vlogging on YouTube as [3Blue1Brown](https://en.wikipedia.org/wiki/3Blue1Brown), Sanderson has an excellent series where he [explained math concepts visually](https://www.youtube.com/channel/UCYO_jab_esuFRV4b17AJtAw)._



