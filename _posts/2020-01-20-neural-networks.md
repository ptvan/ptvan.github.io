---
layout: post
title: Neural networks
---

One lesson I learned in graduate school was the importance of understanding things from first principles. So for learning about neural networks, I really enjoyed reading [Grokking Deep Learning](https://www.manning.com/books/grokking-deep-learning), which implements neural networks using only `numpy`, keeping the reader from being bogged down with implementation details. After that, Michael Nielsen's [Neural Networks and Deep Learning](http://neuralnetworksanddeeplearning.com/) is a good followup. If you prefer watching videos rather than reading, Josh Starmer's [StatQuest Neural Networks playlist](https://www.youtube.com/watch?v=CqOfi41LfDw&list=PLblh5JKOoLUIxGDQs4LFFD--41Vzf-ME1) is also excellent. Another excellent introduction is [this video](https://www.manning.com/livevideo/3blue1brown-neural-networks) from Grant Sanderson*, which also goes into mathematical details.

### General concepts

Like other machine learning systems, neural networks aim to return a set of outputs given some inputs: classes for a image classification task, phrases in the target language for translation task, _etc_.  What makes neural networks unique is the _scale_ of the inputs and outputs and thus the difficulty of training: modern Large Language Models (LLMs) are trained on billions to hundreds of billions of parameters. As a result, progress in Artificial Intelligence (now almost always synonymous with large neural networks) has often involved making the training process more efficient.   

One of the interesting and frustrating problems in modeling complex data is overfitting. The solution often involves a combination of picking the right tools, then knowing how to interpret their output. In a neural network context once you've picked the appropriate [architecture](https://medium.com/data-science/the-mostly-complete-chart-of-neural-networks-explained-3fb6f2367464), the right [activation functions](https://www.analyticssteps.com/blogs/7-types-activation-functions-neural-network), you may need to implement [dropout](http://jmlr.org/papers/v15/srivastava14a.html). These, and other network tuning issues are covered in [Neural Smithing](https://mitpress.mit.edu/books/neural-smithing).

### History and progress

The idea of artificial neural networks has been around since at least 1940s in the form of [Hebbian theory](https://en.wikipedia.org/wiki/Hebbian_theory), though modern artificial neural networks bear only vague conceptual resemblance to their biological analogues. Neural networks gained a lot of attention after Geoffrey Hinton's [famous 1986 paper](https://www.nature.com/articles/323533a0) on _backpropagation_, allowing for quick optimization of gradients, thus enabling multiple parameters to be learned efficiently. 

The availability of big datasets and development of [GPGPUs](https://en.wikipedia.org/wiki/General-purpose_computing_on_graphics_processing_units) accelerated the use of neural networks in many areas, such as [CNNs](https://en.wikipedia.org/wiki/Convolutional_neural_network) in image processing. Another big advance came in 2017 with the [Attention Is All You Need](https://arxiv.org/abs/1706.03762) paper which described Transformer models, enabling the development of [GPTs](https://en.wikipedia.org/wiki/Generative_pre-trained_transformer) which power LLMs. Over time, "neural networks" becomes replaced by the snappier and more marketable name of "AI".

Because they require enormous investments of time, technical expertise and [electrical energy](https://cacm.acm.org/blogcacm/the-energy-footprint-of-humans-and-large-language-models/) there is a lot of interest in making LLMs more efficient. This can take several forms: making LLMs more efficient to train from scratch, making LLMs easier to tweak, speeding up LLM queries, among others. Since many applications only need a small portion of the LLM's weights to be tweaked, rather than all of them to be retrained, techniques like [LoRA](https://medium.com/@raquelhvaz/efficient-llm-fine-tuning-with-lora-e5edb88b64a1) (Low Rank Adaptation) can be used.

As of 2024, one major development is **agentic AI**, smaller programs that _retrieve_ knowledge from LLMs, but can also use _external tools_. In increasing order of sophistication, the major conceptual types of agents are:

- **Simple reflex agents**: reacts to input data via condition-action rules
- **Model-based reflex agents**: remembers previous states in applying condition-action rules
- **Goal-based agents**: works towards higher-level aims which can involve multiple steps
- **Utility-based agents**: evaluates multiple runs of strategy
- **Learning agents**: combines and optimizes strategies over time

Tool use itself can be implemented in multiple ways: **Retrieval-Augmented Generation** (RAG) and **Cache-Augmented Generation** (CAG), optimizing for data freshness or latency, respectively.

### Running neural networks

Because of their value and cost as mentioned above, commercial LLMs are closed-source and operate on a subscription model. Their large size also means these commercial LLMs are cloud-hosted. However, smaller open-source models (still on the order of billions of parameters) can be freely obtained and run locally on a reasonably powerful desktop computer, using tools such as [LM Studio](https://lmstudio.ai/), [Ollama](https://ollama.com/search) or [vLLM](https://github.com/vllm-project/vllm). Many of these tools come with a chat interface, though API access is also available.

### Evaluating neural network performance 

As decision systems, neural networks that perform a narrow, well-defined task like text classification can be evaluated using traditional metrics like accuracy, ROC, _etc_. However, as both neural networks and their tasks become more complex, culminating in general purpose LLMs like ChatGPT, it's important to note that benchmarking them present several unique issues. 

First, because AIs can perform so many tasks, there exists many benchmarks (200 by [one count](https://www.evidentlyai.com/llm-evaluation-benchmarks-datasets)). Choosing one (or more) of these benchmarks to characterize overall "performance" can be tricky, especially when at least for the moment, AIs seem to be significantly [better at some tasks than others](https://www.oneusefulthing.org/p/the-shape-of-ai-jaggedness-bottlenecks).

Second, AIs raise some serious privacy and safety concerns, particularly around [fully autonomous agents](https://arxiv.org/pdf/2502.02649) that motivated separate _safety benchmarks_, testing the AI's susceptibility to illegal, harmful or false information. 

Third, AIs are created to solve then optimize solutions to the problems we pose to them. As a result, sometimes benchmark performance becomes the problem that AIs solve, analogous to students studying to pass standardized tests rather than actually understanding their coursework. In the worst cases, much like these students, AIs can perform well on tests then fail to replicate good performance when [deployed to solve new problems](https://www.youtube.com/watch?v=d5EltXhbcfA).

That being said, there are general-purpose benchmarks like [LLMarena](https://llmarena.ai) and domain-specific benchmarks like [medArena](https://medarena.ai), [BixBench](https://github.com/Future-House/BixBench) and [BioMLBench](https://github.com/science-machine/biomlbench).

*_Vlogging on YouTube as [3Blue1Brown](https://en.wikipedia.org/wiki/3Blue1Brown), Sanderson has an excellent series where he [explained math concepts visually](https://www.youtube.com/channel/UCYO_jab_esuFRV4b17AJtAw).
