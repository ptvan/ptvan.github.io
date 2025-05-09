---
layout: post
title: Neural networks
---

One lesson I learned during graduate school was the importance of understanding things from first principles. So for learning about neural networks, I really enjoyed reading [Grokking Deep Learning](https://www.manning.com/books/grokking-deep-learning), which implements neural networks using only `numpy`, keeping the reader from being bogged down with implementation details. Another excellent introduction is [this video](https://www.manning.com/livevideo/3blue1brown-neural-networks) from Grant Sanderson*, which also goes into mathematical details.  If you prefer watching videos rather than reading, Josh Starmer's [StatQuest Neural Networks playlist](https://www.youtube.com/watch?v=CqOfi41LfDw&list=PLblh5JKOoLUIxGDQs4LFFD--41Vzf-ME1) is also excellent. After that, Michael Nielsen's [Neural Networks and Deep Learning](http://neuralnetworksanddeeplearning.com/) is a good followup.

### General concepts

Like other machine learning systems, neural networks aim to return a set of outputs given some inputs: classes for a image classification task, phrases in the target language for translation task, _etc_.  What makes neural networks unique is the _scale_ of the inputs and outputs and thus the difficulty of training: modern Large Language Models (LLMs) are trained on billions to hundreds of billions of parameters. As a result, progress in Artificial Intelligence (now almost always synonymous with large neural networks) has often involved making the training process more efficient.   

### Accessibility

Since they are very large, commercial-grade LLMs are generally cloud-hosted. Another consideration is licensing: since they require enormous amounts of time, infrastracture, technical expertise and [electrical energy](https://cacm.acm.org/blogcacm/the-energy-footprint-of-humans-and-large-language-models/) to train and run, commercial LLMs are almost always closed-source. However, smaller open-source models (though still on the order of billions of parameters) can be obtained and run locally, such as through [Ollama](https://ollama.com/search).

### A bit of history

The idea of artificial neural networks has been around since at least 1940s in the form of [Hebbian theory](https://en.wikipedia.org/wiki/Hebbian_theory), though modern artificial neural networks bear only vague conceptual resemblance to their biological analogues. Neural networks gained a lot of attention after Geoffrey Hinton's [famous 1986 paper](https://www.nature.com/articles/323533a0) on backpropagation, allowing for quick optimization of gradients, thus enabling multiple parameters to be learned efficiently. 

The availability of big datasets and development of [GPGPUs](https://en.wikipedia.org/wiki/General-purpose_computing_on_graphics_processing_units)s accelerated the use of neural networks in many areas, such as [CNNs](https://en.wikipedia.org/wiki/Convolutional_neural_network) in image processing. Another big advance came in 2017 with the [Attention Is All You Need](https://arxiv.org/abs/1706.03762) paper which described Transformer models, enabling the development of [GPTs](https://en.wikipedia.org/wiki/Generative_pre-trained_transformer).


### Network tuning

One of the interesting and frustrating problems in modeling complex data is overfitting. The solution often involves a combination of picking the right tools, then knowing how to interpret their output. In a neural network context once you've picked the appropriate [architecture](https://medium.com/data-science/the-mostly-complete-chart-of-neural-networks-explained-3fb6f2367464), the right [activation functions](https://www.analyticssteps.com/blogs/7-types-activation-functions-neural-network), you may need to implement [dropout](http://jmlr.org/papers/v15/srivastava14a.html).

[Neural Smithing](https://mitpress.mit.edu/books/neural-smithing) covers some network tuning issues.

*_Vlogging on YouTube as [3Blue1Brown](https://en.wikipedia.org/wiki/3Blue1Brown), Sanderson has an excellent series where he [explained math concepts visually](https://www.youtube.com/channel/UCYO_jab_esuFRV4b17AJtAw).
