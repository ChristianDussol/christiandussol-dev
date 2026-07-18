---
description: >-
  A four-layer framework for the AI agent ecosystem. Foundation, capabilities,
  integration, expertise, and where MCP and Skills actually sit.
---

# The AI Agent Mental Model

## Four layers, and everything clicks

MCP, Agent Skills, AAIF, AGENTS.md. Everyone is talking about AI agents and almost nobody explains how the pieces fit together.

This is the framework I built after a few months in the ecosystem, and it is the one that made the confusion resolve. Four layers, each building on the one below it.

### The four layers

**Layer 1: Foundation.** What makes AI _agentic_. Traditional AI answers. Agentic AI plans, uses tools, acts, and iterates. The difference is autonomy.

**Layer 2: Capabilities.** What agents can _do_. Read data, execute code, create artifacts, search. Tools are the agent's hands and eyes. Without them there is only conversation.

**Layer 3: Integration.** How agents _connect_. MCP is USB for AI agents: write the integration once, and any MCP-compatible agent can use it. Before the standard, you rebuilt the same tool for Claude, then for Cursor, then for ChatGPT.

**Layer 4: Expertise.** How agents _learn_. Tools tell an agent what is available. Skills tell it how to use them well. You can hand someone a toolbox and a manual for the toolbox, and still not have a carpenter.

### Why this page exists

The layers are not academic. Layer 4 is where my series From Prompts to Packages lives, and that series does not fully make sense without this framing. The Skills work is Layer 4 built on Layer 3, on top of the governance described in The Agentic AI Foundation.

The article also works the framework through a single concrete case, a Kubernetes FinOps agent, and shows what changes at each layer. Without Layer 4, the agent tells you to reduce replicas. With it, the agent applies the FinOps methodology: inform, optimize, operate, iterate.

### Read

* **Medium article**: [Lost in the AI Agent Ecosystem? Here's Your Mental Model](https://medium.com/@christian.dussol/lost-in-the-ai-agent-ecosystem-heres-your-mental-model-4e545318207c)
