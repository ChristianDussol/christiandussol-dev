---
description: >-
  A FinOps Skill wired to live OpenCost data through MCP. Identifying real
  waste, generating targeted Kyverno policies, and closing the governance loop.
---

# Part 4: Connecting Skills to the real world via MCP

## Connect: a Skill reaches beyond Claude

Generation and composition happen inside the model. The fourth part takes Skills outside, into the world where data lives. A FinOps Skill pulls real cost data via the Model Context Protocol, analyzes it against governance thresholds, and triggers actions through the policy generator and auditor built earlier in the series.

<figure><img src="../../.gitbook/assets/1 (6).png" alt="" width="563"><figcaption></figcaption></figure>

### What the article covers

* MCP as the integration layer between Skills and live data sources
* A FinOps Skill that queries actual Kubernetes cost data
* The full loop: data → analysis → action, fully composed across three Skills
* Where MCP fits in the agentic AI ecosystem (Layer 3 of the four-layer framework)
* The boundary between deterministic queries and probabilistic reasoning

### Read

* **Medium article**: [Connecting Claude Code Skills to the real world](https://medium.com/@christian.dussol/connecting-claude-code-skills-to-the-real-world-d1d83d6e070e)
* **GitHub**: [github.com/christian-dussol-cloud-native/kyverno/tree/main/skills](https://github.com/christian-dussol-cloud-native/kyverno/tree/main/skills)
