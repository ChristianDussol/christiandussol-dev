---
description: >-
  Azure decision guides across the AZ-305 domains. Decision matrices, cost
  trade-offs, and the anti-patterns that look reasonable and are not.
---

# Azure Architecture Decision Guides

## Decision matrices, not feature tables

The AZ-305 does not ask _"What is Azure Cosmos DB?"_ It asks _"A global e-commerce company needs sub-millisecond read latency across five continents with strong consistency for inventory management. Evaluate the data solution."_

The exam assumes you know the services exist. It tests whether you can choose. Most study material prepares you for the wrong exam, which is why I ended up writing my own.

These guides are structured around the choice rather than the catalogue. Each one carries the trade-off analysis, the cost implications, and the anti-patterns: the options that look reasonable and are not. They also carry the question most architecture comparisons ignore, which is team capability. The technically superior service is the wrong answer when nobody on the team can operate it.

### The guides

| Guide                         | What it covers                                     |
| ----------------------------- | -------------------------------------------------- |
| **Compute Services**          | AKS, Container Apps, Functions, Logic Apps, VMs    |
| **Storage Services**          | Storage Accounts, Cosmos DB, Data Lakes, Synapse   |
| **Azure SQL Services**        | SQL Database, SQL Managed Instance, SQL on VMs     |
| **Networking Services**       | VNet, Application Gateway, Front Door, VPN Gateway |
| **Messaging and Analytics**   | Service Bus, Event Grid, Event Hubs, Data Factory  |
| **Security and Identity**     | Entra ID, RBAC, Key Vault, policy enforcement      |
| **Monitoring and Governance** | Azure Monitor, Azure Policy, Cost Management       |

→ [GitHub: Azure Architecture Decision Guides](https://github.com/christian-dussol-cloud-computing/microsoft-azure/blob/main/certifications/AZ-305/architecture-decision-guides/README.md)

### The three frameworks behind them

**The four-pillar decision matrix.** Performance, cost, complexity, risk. Every scenario question breaks down through these four lenses, and so does every real architecture decision.

**Service-to-scenario mapping.** Decision trees instead of feature lists. You stop asking what a service does and start asking what the constraints rule out.

**Anti-pattern recognition.** The exam offers attractive wrong answers, and they are attractive because they are the same mistakes people make in production. Cosmos DB for simple CRUD. Functions for long-running batch. AKS when the team has no container expertise. Premium tiers in dev.

### Why this outlasts the exam

The same matrix works for AWS Lambda versus Azure Functions versus Cloud Functions. It works for AI services. It works for anything where you have to choose under constraint and defend the choice afterwards.

And when a stakeholder asks why you chose this solution, you can articulate the decision process rather than reciting the feature list. That difference is the whole job.

### Read

* **Medium article**: [Beyond Memorization: How Architectural Thinking Skills Transform AZ-305 Exam Success](https://medium.com/@christian.dussol/beyond-memorization-how-architectural-thinking-skills-transform-az-305-exam-success-9ed69c14150f)
