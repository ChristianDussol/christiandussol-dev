---
description: >-
  Wiring an agent through MCP takes a few lines. Governing what it may ask, how
  often, and proving what it did, is the real work.
---

# Episode 1: MCP

### **Connecting an agent is the easy part**

Connecting an agent to your cloud costs is a few lines of code. Deciding what it may ask, how often, and whether an auditor can trace it six months later is the real work.

This episode is in three parts: what MCP is and how it works, what building a governed one on top of real cost data taught me about where the protocol stops, and what the July 28 revision changed about where that boundary now sits.

<figure><img src="https://3864580007-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F782Y46kG3IDKMjaaCmCh%2Fuploads%2Fzgyjo6HxQU7JaPBbRGxE%2F1.png?alt=media&#x26;token=2940f1f3-b8d4-4d01-b138-9029ba270d5a" alt=""><figcaption></figcaption></figure>

### Part one: what MCP is

For a reader who has not built one. The M×N problem it solves, three agents and three tools being nine bespoke integrations rather than three. The three primitives, tools, resources and prompts. Discovery through `tools/list` and `tools/call`, defined by the protocol rather than left to each integration.

Then the line the rest of the piece rests on: **the protocol carries the call, not the decision.** Over HTTP it can authenticate who connected, as an OAuth 2.1 resource server. It never sees the reasoning that produced the call. MCP standardises the connection, and leaves four things it does not settle on its own: identity, authorization, audit, cost.

### Part two: what building a governed one taught me

A server exposing Kubernetes cluster costs from OpenCost to an agent, under least privilege, audit and a call budget. It runs offline on synthetic data and against a real OpenCost install on a local cluster.

* **MCP on the agent side, REST on the data side.** Chaining to OpenCost's own MCP server would have been protocol for its own sake: tool discovery and negotiation for a hop no agent observes
* **Least privilege has to be declared, not only enforced.** Without annotations, MCP assumes the worst on a tool's behalf. Three read-only tools appeared in the Inspector as writes that could be destructive. Found by looking at the server from the outside, with the protocol's own tool
* **The call budget, and where a limit belongs.** It works inside one process and fails behind a load balancer. Not badly coded, badly placed. The revision published on July 28 did not create that limit and does not fix it: it removed what used to hide it
* **One word, three questions.** Identity, quota and domain legitimacy do not live in the same layer. The build covers three of the four. Identity is the one it leaves implicit, because local is where it started

→ **Read it**: [Medium](https://medium.com/@christian.dussol/connecting-an-agent-is-the-easy-part-what-building-a-governed-mcp-server-taught-me-d333f1e82365) · [LinkedIn Pulse](https://www.linkedin.com/pulse/connecting-agent-easy-part-what-building-governed-mcp-dussol-xnwse/)

📎 **See it**: [AAIF Project Focus: MCP carousel (PDF)](https://github.com/christian-dussol-ai-native/model-context-protocol/blob/main/carousel/aaif-project-focus-mcp.pdf)

→ **Run it**: [model-context-protocol](https://github.com/christian-dussol-ai-native/model-context-protocol) on GitHub, and [The agentic layer](../../labs/the-agentic-layer.md) in Labs

### Part three: what the July 28 revision changed

The build hit a limit in the wrong place. Three days later, the protocol shipped its largest change since launch, and the first under foundation governance. Read separately it looks like six changes. Read together it describes one movement: **the core gets smaller, and most of what leaves it does not disappear. It moves somewhere it can be held.**

* **The property was already there.** MCP speaks JSON-RPC 2.0, whose 2010 specification opens by calling itself stateless. The revision is not converging on someone else's standard, it is returning to a property of the thing it was already built on
* **Six times the core got smaller.** The handshake goes, routing moves to headers, the cache borrows Cache-Control, state becomes an explicit argument, the logging leaves. Even the missing-resource error falls back to the standard JSON-RPC code, which nobody else will write about and which is the whole movement in miniature
* **The one that says the most.** What replaces MCP's own logging is OpenTelemetry, with W3C Trace Context propagation fixed in the specification. Not an analogy: the same standard, the same key names, the same tooling the rest of the industry already runs. **MCP did not invent a new way to observe. It stopped trying**
* **Where the capability went.** Reading the six as removals misses half the revision. Capability moved into extensions, into the payload, into the infrastructure. Three directions, each a layer that can actually own what it receives. **This is not a protocol giving up. It is a protocol sorting**
* **Two other readings.** Eleanor Lee reads the revision as a market document, asking who gains and who absorbs the cost, and supplies an answer to "why now" that the specification itself does not. Akamai's threat research team arrives at the same place from the security side

What the protocol stops specifying does not stop being required. When MCP carried sessions, sessions were its problem. Identity, quota and audit are now yours to place. **The specification got lighter. The governance did not.**

→ **Read it**: [Medium](https://medium.com/@christian.dussol/mcps-july-28-revision-a-lighter-protocol-a-larger-ecosystem-3cca681e7b88) · [Primary source](https://blog.modelcontextprotocol.io/posts/2026-07-28/)

📎 **See it**: [A lighter protocol, a larger ecosystem carousel (PDF)](https://github.com/christian-dussol-ai-native/model-context-protocol/blob/main/carousel/AAIF%20Project%20Focus%20-%20MCP%20-%20A%20lighter%20protocol%2C%20a%20larger%20ecosystem.pdf)

***

Fewer risks in the protocol. More of them in your implementation.

**New technology. Same operational questions.**

Next in the series: AGENTS.md, the convention for giving an agent its instructions, built on this same server.
