---
layout: post
title: Building AI apps
---

As a technology matures, the focus gradually shifts from pure research to development tasks such as deploying, scaling and benchmarking. While some forms of AI such as the ChatGPT website have been accessible to non-programmers for a while, AI application development for specific domains have also progressed significantly. And while I think there is still much progress to be made by AI _researchers_, it's fun to learn some of the things dealt with by AI _developers_ if you were thinking about an AI-powered app yourself in 2025.

### Implementing a backend to query LLMs: APIs and vector databases

The major AI vendors host LLMs on their own hardware which users can access via RESTful APIs after buying access tokens. Alternatively, as I mentioned previously, you can also download open-source LLMs and [run them locally](https://ptvan.github.io/neural-networks/). Using this approach, you don't need access tokens and your queries and results remain on your computer. You can launch an LLM and interact with it directly on your local machine using the Ollama client, which is sending and receiving REST requests locally under the hood (vLLM and LLM Studio work similarly). This Ollama chat interface can feel like a functional app already: you can ask the LLM being run to do sentiment analysis on a text passage, or describe an image without writing a single line of code.

In addition to these vendor-provided RESTful APIs, which you can access through Python libraries like [LangChain](https://python.langchain.com/docs/introduction/), the opaquely-named **Model Context Protocol** (or simply [MCP](https://modelcontextprotocol.io/)) bills itself as "the USB-C port of AI applications" by providing SDKs for common LLM tasks in popular languages (the name is less opaque when you realize "Model" here refers to LLMs). In addition to serving API calls, MCP also features _dynamic self discovery_, asking the LLM it interfaces with what functionalities are available, and making those accessible to the programmer. 

Typical of application development, you'll need your AI app to store and retrieve data. Since many LLM operations depend on vectors (particularly embeddings), you'll want to implement a _vector database_ such as [Chroma](https://www.trychroma.com/), [Pinecone](https://www.pinecone.io/) or [Milvus](https://milvus.io/), _etc_. Here's a quick high-level [comparison of vector databases](https://medium.com/@EjiroOnose/vector-database-what-is-it-and-why-you-should-know-it-ae7e7dca82a4).

### Putting a pleasant frontend on your AI app: Gradio

Once you have started querying an LLM and getting results back, you technically have your first AI app. However, these prototypes are usually Python scripts or IPython notebooks that are a little clumsy to use. Streamlit is a common framework for Python apps, as I have [written previously](https://ptvan.github.io/Python-interactive-dataviz/), and can also be used for AI apps. Another option is using [Gradio](https://www.gradio.app/) to embed interactive elements in your notebook, or have the entire app be a stand-alone webpage.

### Incorporating agents

In 2025, many AI apps involve an _agent_, which retrieves knowledge from LLMs but also use tools to augment or update this knowledge. One such augmentation scheme is **Retrieval Augmented Generation** (RAG), where additional new information is retrieved by the AI app and used to generate output. Depending on the size and frequency of these retrievals, **Cache Augmented Generation** (CAG) can be more appropriate than RAG, as discussed [here](https://www.youtube.com/watch?v=HdafI0t3sEY). You can also use more than one agent in a _multi-agent system_, which requires _orchestration_. 

In building these systems, Anthropic (who created MCP) has some [recommendations](https://www.anthropic.com/engineering/building-effective-agents). The same article also listed some agent frameworks current at the time: [Rivet](https://rivet.ironcladapp.com), [Vellum](https://www.vellum.ai/) and [Amazon Bedrock Agents](https://aws.amazon.com/bedrock/agents/). My former colleague Dan told me about [PydanticAI](https://github.com/pydantic/pydantic-ai) which was great fun to play around in. 

### Benchmarking your AI app

Another common task in application development is measuring performance, and there are many benchmarks available depending on the task the AI app is performing, as well as benchmarks for its safety: [SWE-bench](https://github.com/SWE-bench/SWE-bench) is commonly used for coding agents, [AI2 ARC](https://huggingface.co/datasets/allenai/ai2_arc) for question answering, [WinoGrande](https://winogrande.allenai.org/) for math, [HarmBench](https://github.com/centerforaisafety/HarmBench) for assessing AI safety, among others.

### Weekend project: AIBookButler

I had written previously that [recommender systems](https://ptvan.github.io/recommender-systems/) are really interesting, and while they don't need AI features to work well, I wanted to use a recommender as a project to explore AI tools. 

Since I loved using Pandora in college, my first idea was an AI music recommender. But a bit of digging revealed two problems: music that is royalty-free and contains robust metadata is scarce, and audio data has many higher-order acoustic and temporal properties that greatly increases the number of features the recommender have to train on. An accurate and useful general-purpose music recommender would take money (not to mention licensing headache for commercial music) and time, too much for a weekend project.

So instead I put together **AIBookButler** in a long afternoon. The app takes some publicly available book metadata (title, author, synopsis, _etc_ but not the full text itself), cleans them (which unsurprisingly removes a lot of the entries) and loads them into a vector database (I used [Chroma](https://python.langchain.com/docs/integrations/vectorstores/chroma/)) with some text embeddings using LangChain. This allows the database to be queried using similarity search which returns books related to your query. As you can see in my [repo](https://github.com/ptvan/AIBookButler), this doesn't take very much code, the majority of which is data cleaning. This is one area where AI overlaps with old-school data science: _garbage in, garbage out_. 

A fun follow-up would be to make a chatbot that ingests a book's full text (likely from [project Gutenberg](https://www.gutenberg.org/)) and discusses the contents with you, making its "Book Butler" name a bit more accurate. 