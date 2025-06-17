---
layout: post
title: Building AI apps
---

As a technology matures, the focus gradually shifts from pure research to development tasks such as deploying, scaling and benchmarking. 
Parallel to the [intense general AI usage by non-programmers](https://www.interconnects.ai/p/people-use-ai-more-than-you-think), tools for AI application development have also progressed significantly in the last few years. And while I think there is still much progress to be made by AI _researchers_, it's fun to learn some of the things dealt with by AI _developers_ if you were thinking about building an AI-powered app yourself in 2025.

### Implementing a backend to query LLMs: APIs and vector databases

The major AI vendors host LLMs on their own hardware which users can access via RESTful APIs after buying access tokens. Alternatively, as I mentioned previously, you can also download open-source LLMs and [run them locally](https://ptvan.github.io/neural-networks/). Using this approach, you don't need access tokens and your queries and results remain on your computer. You can launch an LLM and interact with it directly on your local machine using the Ollama client, which is sending and receiving REST requests locally under the hood (vLLM and LLM Studio work similarly). This Ollama chat interface can feel like a functional app already: you can ask the LLM being run to do sentiment analysis on a text passage, or describe an image without writing a single line of code.

In addition to these vendor-provided RESTful APIs, which you can access through Python libraries like [LangChain](https://python.langchain.com/docs/introduction/) and [PydanticAI](https://github.com/pydantic/pydantic-ai) (introduced to me by my former colleague Dan), the opaquely-named **Model Context Protocol** (or simply [MCP](https://modelcontextprotocol.io/)) bills itself as "the USB-C port of AI applications" by providing SDKs for common LLM tasks in popular languages (the name is less opaque when you realize "Model" here refers to LLMs). In addition to serving API calls, MCP also features _dynamic self discovery_, asking the LLM it interfaces with what functionalities are available, and making those accessible to the programmer. 

Typical of application development, you'll need your AI app to store and retrieve data. Since many LLM operations depend on vectors (particularly embeddings), you'll want to use a _vector database_ like [Chroma](https://www.trychroma.com/), [Pinecone](https://www.pinecone.io/), [Milvus](https://milvus.io/), _etc_. Here's a quick high-level [comparison of vector databases](https://medium.com/@EjiroOnose/vector-database-what-is-it-and-why-you-should-know-it-ae7e7dca82a4).

### Putting a pleasant frontend on your AI app: Gradio

Once you have started querying an LLM and getting results back, you technically have your first AI app. However, these prototypes are usually Python scripts or IPython notebooks that are clumsy to use. Streamlit is a common framework for Python apps, as I have [written previously](https://ptvan.github.io/Python-interactive-dataviz/), and can also be used for AI apps. Another option is using [Gradio](https://www.gradio.app/) to embed interactive elements in your notebook, or have the entire app be a stand-alone webpage.

### Building more complex AI apps: workflows and agents

As your app becomes more complex, it's good to consider how you would architect future iterations. Anthropic (who created MCP) has some [useful observations and recommendations](https://www.anthropic.com/engineering/building-effective-agents): you should start building apps up using _workflows_ which chain several LLMs or LLM-querying parts together. This simple design means you can see if any of the parts are malfunctioning, easing troubleshooting. As your app grows more complicated, perhaps the parts can augment the knowledge you get from the LLM(s). One such augmentation scheme is **Retrieval Augmented Generation** (RAG), where additional new information is retrieved by the AI app and used to generate final output. Depending on the size and frequency of these data retrievals, **Cache Augmented Generation** (CAG) can be more appropriate than RAG, as discussed [here](https://www.youtube.com/watch?v=HdafI0t3sEY). 

Eventually, you will encounter a use case where simply chaining tools together isn't enough: maybe the output from your tools aren't predictable, or the steps in your workflow change dynamically depending on input. In that situation, you may move beyond workflows onto _agents_, which can cope with this uncertainty but are also more complex. You can even use more than one agent in a _multi-agent system_, which requires _orchestration_. 

In building these systems, Anthropic also listed some agent frameworks available at the time: [Rivet](https://rivet.ironcladapp.com), [Vellum](https://www.vellum.ai/) and [Amazon Bedrock Agents](https://aws.amazon.com/bedrock/agents/), though likely there will be others as time goes on.

### Benchmarking your AI app

Another common task in application development is measuring performance, and there are many benchmarks available depending on the task the AI app is performing, as well as benchmarks for its safety: [SWE-bench](https://github.com/SWE-bench/SWE-bench) is commonly used for coding agents, [AI2 ARC](https://huggingface.co/datasets/allenai/ai2_arc) for question answering, [WinoGrande](https://winogrande.allenai.org/) for math, [HarmBench](https://github.com/centerforaisafety/HarmBench) for assessing AI safety, among others.

### Weekend project: AIBookButler

I had written back in 2019 that [recommender systems](https://ptvan.github.io/recommender-systems/) are really interesting, and while they haven't needed AI to work well (in that post I built a basic movie recommender using Spark and scikit-learn), I wanted to make another recommender from scratch as a project to explore AI tools. 

Since I loved using Pandora in college, I thought about an AI music recommender. But a bit of digging revealed two problems: music that is royalty-free and contains robust metadata is scarce, and audio data has many higher-order acoustic and temporal properties that greatly increases the number of features the recommender has to train on. An useful, accurate general-purpose music recommender would take money and time, not to mention the headaches involved in licensing commercial music. All this means it's too much for a weekend project.

So instead I put together the beginnings of **AIBookButler** in a long afternoon. The app takes some book metadata (title, author, synopsis, _etc_ but not the full text itself) and loads them into a vector database (I used [Chroma](https://python.langchain.com/docs/integrations/vectorstores/chroma/)) with some text embeddings using LangChain. This allows the database to be queried using similarity search which returns books related to your query. As you can see in [the project repo](https://github.com/ptvan/AIBookButler), this doesn't require very much code, partly because I used a very small subset of a [public Kaggle dataset](https://www.kaggle.com/datasets/dylanjcastillo/7k-books-with-metadata) which required minimal data cleaning. This is something AI projects have in common with old-school data science: _garbage in, garbage out_. If this been a production tool with millions of rows of input, the project would have needed a significant amount of data cleaning. 

Another part of the app performs some sentiment analysis on text that the user enters. This was simply a matter of wrapping Streamlit around LLM chat functionality, though later it would be nice to train the LLM on books it hasn't been exposed to. 

