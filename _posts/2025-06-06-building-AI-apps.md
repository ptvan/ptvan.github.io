---
layout: post
title: Building AI apps
---

As competition between different LLMs rages on, it's interesting to speculate how they (or rather, the companies that make them) will differentiate. At the same time, if you're a developer, these differences are a little annoying because programmers love abstraction. LLMs are evolving very fast, so unless you're committing to a single LLM vendor, discovering that the code you wrote for one LLM doesn't work for another is annoying. Thankfully, there are solutions to this abstraction problem. These solutions are also evolving, ...of course.

### Abstraction and standardization are your friends: APIs and MCP

As I mentioned [previously](https://ptvan.github.io/neural-networks/), Ollama makes obtaining and updating open-source LLMs much simpler, which is great given how many are available. You can also launch an LLM and chat with it directly on your local machine, which is also helpful if you don't want to buy tokens just to prototype an app.

For programmatic access, the major LLM vendors use RESTful APIs since the requests will be coming over HTTP. In addition to these APIs, the opaquely-named **Model Context Protocol** (or simply [https://modelcontextprotocol.io/](MCP)) bills itself as "the USB-C port of AI applications" and accomplishes this by providing SDKs for common LLM tasks in popular languages (the name is less opaque when you realize "Model" here refers to LLMs). In addition to serving API calls, MCP also features _dynamic self discovery_, asking the LLM it interfaces with what functionalities are available, and making those accessible to the programmer. 

### The Age of Agents

In 2025, the AI app you create will likely involve an agent, which has the knowledge of LLMs and can also use tools. In increasing order of sophistication, the major conceptual types of agents are:

- **Simple reflex agents**: reacts to input data via condition-action rules
- **Model-based reflex agents**: remembers previous states in applying condition-action rules
- **Goal-based agents**: works towards higher-level aims which can involve multiple steps
- **Utility-based agents**: evaluates multiple runs of strategy
- **Learning agents**: combines and optimizes strategies over time

Of course you can also use more than one agent in a _multi-agent system_, which requires _orchestration_. In building these systems, Anthropic (who created MCP) recommends that you use "[simple, composable patterns rather than complex frameworks](https://www.anthropic.com/engineering/building-effective-agents)". In the same blogpost they also listed several frameworks: LangGraph, Rivet, Vellum and Amazon Bedrock Agents. My friend and former colleague Dan told me about [PydanticAI](https://github.com/pydantic/pydantic-ai) which was great fun to play around in. 

