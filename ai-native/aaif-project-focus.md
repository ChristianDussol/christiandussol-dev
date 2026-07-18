---
description: >-
  A series on the agentic layer, project by project, with a working build at
  each step. MCP, AGENTS.md, goose, and why the standards came first.
---

# AAIF Project Focus

## The agentic layer, project by project, with a working build at each step

Deploying an agent today is still mostly bespoke. Each framework speaks its own protocol to tools and data. Each carries its own conventions for how the agent should behave, where it reads its instructions, what it is allowed to touch. Move from one repo to the next and the wiring changes underneath you.

It works in a demo. It does not yet compose into infrastructure I would want to run, audit, and bill in production.

That gap is what an open foundation exists to close before fragmentation sets in.

***

### Why the standards came first

**The arc-opener.** Before the deep dives, how the problem looks from a regulated financial-services seat, and why a foundation forming around it caught my attention.

The agentic layer is the fastest-moving floor of the substrate, and that speed is both the whole point and the whole risk. A capability moving this fast can fragment before it standardizes: a dozen incompatible protocols, each with its own lock-in, the way the early cloud had a dozen incompatible APIs.

**The direction is set. The speed is not.** That is the part still being decided, and it is being decided now.

The Agentic AI Foundation started with three founding projects, contributed by three competing companies, which is precisely what makes the neutrality credible. They divide the problem cleanly:

* **MCP** (Anthropic) is **connection**: how an agent reaches the tools and data outside itself, through one protocol instead of a dozen bespoke integrations
* **AGENTS.md** (OpenAI) is **behavior**: a predictable place to give an agent its context and instructions, so conduct does not have to be re-learned per repo
* **goose** (Block) is **execution**: the harness that actually runs the agent, local-first and LLM-agnostic, an MCP client you can point at any model

Connection, behavior, execution. Three complementary layers, not three competing products. And worth noting: these are building blocks, not agent frameworks. Frameworks can compete above them. The building blocks benefit from being shared and stable rather than fought over.

Then a fourth arrived in mid-2026: **agentgateway**, contributed by Solo.io. Not an afterthought, but what the pattern would predict. Once connection, behavior and execution are in place, the next thing you need is the operational layer that governs them all.

→ **Read the arc-opener**: [Medium](https://medium.com/@christian.dussol/aaif-project-focus-series-why-the-standards-came-first-1dccce7606ea) · [LinkedIn Pulse](https://www.linkedin.com/pulse/aaif-project-focus-series-why-standards-came-first-christian-dussol-ao3be)

***

### Why a regulated seat watches this closely

Deploying an agent is the easy part. Operating it under constraint is the work. Which identity does it act under. What is it allowed to touch. How is every action logged so an auditor can trace it months later.

Concretely: an agent permitted to read positions but never to place an order. Another allowed to summarize a document but never to reach a payment system. Those boundaries belong in infrastructure you can audit, not in a prompt you hope holds.

**The interesting question is no longer whether an agent can call a tool. It is whether that call can become governed infrastructure: identified, scoped, logged.**

***

### The series

Project by project, with a working build at each step rather than a description.

#### Episode 1: MCP

Wiring an agent to a system you cannot afford to get wrong. The connection layer, made concrete.

#### Episode 2: AGENTS.md

Making agent behavior predictable and reviewable.

#### Episode 3: goose

Running a local-first agent against your own tools and models. Where the three building blocks converge.

***

_The projects will keep moving. Some of what is true about this layer today will not be in a year. The question underneath will hold: whether the open infrastructure for agents takes shape fast enough, and what it asks of the organizations that have to run agents within real cost and governance constraints._
