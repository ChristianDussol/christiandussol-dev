---
description: >-
  Anthropic, OpenAI and Block put MCP, goose and AGENTS.md under the Linux
  Foundation. The CNCF playbook, applied to agentic AI.
---

# The Agentic AI Foundation

## Three competitors, one foundation, and a pattern we have seen before

In 2014, container orchestration was fragmented. Docker Swarm, Mesos, Diego, Kubernetes, all incompatible. Enterprises were paralysed by choice. Then the CNCF arrived in 2015 with neutral governance, and the rest is a decade of cloud-native history.

On December 9, 2025, the Linux Foundation announced the Agentic AI Foundation. Anthropic, OpenAI and Block, three direct competitors, co-founded it and donated their core projects to it. Backed by AWS, Google, Microsoft, Bloomberg and Cloudflare.

The playbook is not new. That is exactly why it is worth paying attention to.

### What the article covers

* **The three founding projects and what each solves.** MCP, the universal connector, donated by Anthropic with over ten thousand servers already published. goose, Block's local-first agent framework, effectively Minikube for AI agents. AGENTS.md, OpenAI's convention for predictable agent behavior, adopted by sixty thousand projects in four months
* **The "last mile" problem.** We have powerful models. We have Kubernetes and cloud platforms. What we lacked was the standardized connection layer between agents and enterprise systems. Without MCP, every integration is custom, multiplied by every agent you use
* **Why financial services care first.** Bloomberg is a Platinum member for a reason. You cannot connect agents to production systems without authentication, audit trails, data lineage, and compliance logging. MCP provides these as protocol features rather than custom add-ons
* **The foundation pattern, three times over.** Linux in the 2000s. Kubernetes in the 2010s. Agentic AI in the 2020s. Pre-competitive protocols create markets, which is why competitors cooperate at this layer
* **What it means for platform engineers.** MCP integration becomes expected rather than optional. Agent composition becomes practical, which is the microservices pattern applied to AI. Compliance frameworks can finally scale, because you approve the pattern once. And a new FinOps problem arrives, because agent-to-agent communication has a cost nobody is watching yet

### Read

* **Medium article**: [The Agentic AI Foundation: Why 3 Competitors Just Changed the AI Landscape](https://medium.com/@christian.dussol/the-agentic-ai-foundation-why-3-competitors-just-changed-the-ai-landscape-b7f762bdc238)
