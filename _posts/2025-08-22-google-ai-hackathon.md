---
layout: post
title: Google Cloud AI Hackathon
tags:
 - 5 min read
---

## Experience
---

I was invited to participate in the AI Hackathon organized by Google Cloud, where I had the opportunity to know, explore and use AI models built by Google.
At these times, I was not familiar with new concepts like [Large Language Models (LLMs)](https://en.wikipedia.org/wiki/Large_language_model "Large Language Models - AI models that can understand and generate human language") and [Generative AI](https://en.wikipedia.org/wiki/Generative_artificial_intelligence "Generative AI - AI systems that can generate new content"), [MCP (Model Context Protocol)](https://modelcontextprotocol.io/ "Model Context Protocol - Open standard for AI model integration") and ADK (Agent Development Kit).
Google Cloud provided a set of tools and resources to help me build and deploy AI agents using [BigQuery](https://cloud.google.com/bigquery "BigQuery - Google Cloud's data warehouse for analytics"), [Vertex AI](https://cloud.google.com/vertex-ai "Vertex AI - Google Cloud's machine learning platform"), and [Cloud Run](https://cloud.google.com/run "Cloud Run - Google Cloud's serverless container platform").

I was fascinated about how we can create AI agents that can help us to solve problems and improve our productivity, not only in the development process but also for any context.
I realized that we need somehow understand how to integrate these new techonologies with our current systems and processes, it is easy to deep dive into this but we need to be careful with the risks and limitations.

Google Cloud has invested a lot of resources to build and use different kind of techonlogies focused on AI, that means we can have different solutions for orchestrators, large databases, microservices, and APIs.

<br>

<img src="../assets/images/hackathon.jpg" alt="Google Cloud AI Hackathon" style="
  display: block;
  margin-left: auto;
  margin-right: auto;
  width: 50%;
  max-width: 400px;
  height: auto;"
/>

<br>

## From LLMs to Agents: A Recap of the Hackathon
---

We explored how to move beyond basic Large Language Models (LLMs) to build goal-oriented AI agents. The hackathon was structured around hands-on workshops, technical sessions, and collaborative coding sessions that gave us practical experience with cutting-edge AI technologies. Over the course, we learned about the evolution of AI systems and how Google Cloud is positioning itself at the forefront of this transformation.
<br>
<br>

### The Evolution of AI
---

AI agents represent the next step in the evolution of AI. While traditional LLMs are great for generating text and [retrieval-augmented generation (RAG)](https://en.wikipedia.org/wiki/Retrieval-augmented_generation "Retrieval-Augmented Generation - AI technique that combines text generation with information retrieval") adds external data, agents go a step further. They are applications that perceive, decide, and act to achieve a specific goal. This is made possible by giving them access to tools like APIs and databases.

The key difference is that agents don't just respond to prompts—they can take autonomous actions, make decisions based on context, and work towards specific goals. This represents a paradigm shift from reactive AI systems to proactive, goal-oriented systems that can handle complex workflows and multi-step processes.
<br>
<br>

### The Agent Development Kit (ADK)
---

The [Agent Development Kit (ADK)](https://cloud.google.com/vertex-ai/docs/agents "Agent Development Kit - Google's SDK for building AI agents") is Google's tool for building these advanced AI systems. It's a client-side SDK that helps developers create and customize multi-agent applications for complex, real-world scenarios.

The kit includes a ecosystem of pre-built tools and connectors, making it easier to integrate with various data sources, APIs, and external services.

During the hackathon, we got hands-on experience with ADK's multi-agent capabilities, which allow multiple agents to work together on complex tasks. The framework also includes built-in support for defining agents and their tools with minimal boilerplate code, significantly reducing development time and complexity.
<br>
<br>

### The Model Context Protocol (MCP)
---

The [Model Context Protocol (MCP)](https://modelcontextprotocol.io/ "Model Context Protocol - Open standard for AI model integration") is a revolutionary open standard that acts as a "USB-C port" for AI models. This protocol bridges the gap between AI models and external data sources and tools, simplifying how LLMs get context and execute actions.

MCP's design philosophy is centered around interoperability and standardization. It provides a common interface that allows different AI models to connect to various tools, APIs, and resources with structured inputs and outputs. This means developers can build tools once and use them across different AI platforms and models.

During the hackathon, we explored how MCP enables seamless integration between AI agents and external systems. The protocol supports both synchronous and asynchronous operations, making it suitable for real-time applications as well as batch processing scenarios.
<br>
<br>

### Building Agents on Google Cloud
---

During the hackathon, I learned there are several ways to build agents on Google Cloud, each suited for different users and use cases.

**Platforms and Tools:**

- [Building Agents on Google Cloud](https://cloud.google.com/vertex-ai/docs/agents "Building Agents on Google Cloud - Google Cloud's platform for creating AI agents"): The foundational platform that provides the infrastructure and services needed for agent development and deployment.

- [Agentspace](https://cloud.google.com/vertex-ai/docs/agentspace "Agentspace - Google Cloud's no-code UI for building AI agents"): A no-code UI designed specifically for business users who want to build agents focused on internal employee productivity without writing code.

- [ADK + Vertex AI Agent Engine](https://cloud.google.com/vertex-ai/docs/agents "ADK + Vertex AI Agent Engine - Google's recommended path for building AI agents"): The recommended path for developers who want full control over their agent implementations. This combination allows developers to use Google's client-side ADK for building agents and deploy them on a fully-managed runtime.

**Data Integration:**

We also explored how to connect agents to [BigQuery](https://cloud.google.com/bigquery "BigQuery - Google Cloud's data warehouse for analytics"), Google Cloud's powerful data warehouse for real-time structured data. This integration can be achieved through custom function tools with Python code or by leveraging the [ADK](https://cloud.google.com/vertex-ai/docs/agents "Agent Development Kit - Google's SDK for building AI agents")'s built-in connectors.

The hackathon demonstrated how these different approaches can be combined to create sophisticated AI applications that can process large datasets, make intelligent decisions, and automate complex business processes.
<br>
<br>

## Conclusion

[A huge thank you to the Google Cloud Team for this incredible opportunity!](https://www.linkedin.com/feed/update/urn:li:activity:7361727319628988416)

This hackathon was transformative, providing me with a comprehensive understanding of the powerful tools available on Google Cloud for building AI agents. The combination of [ADK](https://cloud.google.com/vertex-ai/docs/agents "Agent Development Kit"), [MCP](https://modelcontextprotocol.io/ "Model Context Protocol"), and [Vertex AI](https://cloud.google.com/vertex-ai "Vertex AI") creates a scalable framework for developing sophisticated AI applications.

<img src="../assets/images/google-campus-bike.jpg" alt="Google Cloud" style="
  display: block;
  margin-left: auto;
  margin-right: auto;
  width: 30%;
  max-width: 300px;
  height: auto;"
/>
