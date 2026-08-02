# Episode 1: MCP

**Connecting an agent is the easy part.**

Connecting an agent to your cloud costs is a few lines of code. Deciding what it may ask, how often, and whether an auditor can trace it six months later is the real work.

This episode is in two parts: what MCP is and how it works, then what building a governed one on top of real cost data taught me about where the protocol stops.

### 📎 Visual companion

[AAIF Project Focus: MCP carousel (PDF)](https://github.com/christian-dussol-ai-native/model-context-protocol/blob/main/carousel/aaif-project-focus-mcp.pdf)

### Part one: what MCP is

For a reader who has not built one. The M×N problem it solves, three agents and three tools being nine bespoke integrations rather than three. The three primitives, tools, resources and prompts. Discovery through `tools/list` and `tools/call`, defined by the protocol rather than left to each integration.

Then the line the rest of the piece rests on: **the protocol carries the call, not the decision.** Over HTTP it can authenticate who connected, as an OAuth 2.1 resource server. It never sees the reasoning that produced the call. MCP standardises the connection, and leaves four things it does not settle on its own: identity, authorization, audit, cost.

### Part two: what building a governed one taught me

A server exposing Kubernetes cluster costs from OpenCost to an agent, under least privilege, audit and a call budget. It runs offline on synthetic data and against a real OpenCost install on a local cluster.

* **MCP on the agent side, REST on the data side.** Chaining to OpenCost's own MCP server would have been protocol for its own sake: tool discovery and negotiation for a hop no agent observes
* **Least privilege has to be declared, not only enforced.** Without annotations, MCP assumes the worst on a tool's behalf. Three read-only tools appeared in the Inspector as writes that could be destructive. Found by looking at the server from the outside, with the protocol's own tool
* **The call budget, and where a limit belongs.** It works inside one process and fails behind a load balancer. Not badly coded, badly placed. The revision published on July 28 did not create that limit and does not fix it: it removed what used to hide it
* **One word, three questions.** Identity, quota and domain legitimacy do not live in the same layer. The build covers three of the four. Identity is the one it leaves implicit, because local is where it started

### Read the field note

* **LinkedIn Pulse**: [Connecting an agent is the easy part: What building a governed MCP server taught me](https://www.linkedin.com/pulse/connecting-agent-easy-part-what-building-governed-mcp-dussol-xnwse/)
* **GitHub**: [model-context-protocol](https://github.com/christian-dussol-ai-native/model-context-protocol)
* **Runnable lab**: The agentic layer

Next in the series: AGENTS.md, the convention for giving an agent its instructions, built on this same server.
