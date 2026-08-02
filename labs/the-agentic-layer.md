---
description: >-
  A governed MCP server and three composable Kyverno Skills. Where the boundary
  lives in auditable infrastructure rather than in a prompt you hope holds.
---

# The agentic layer

The top floor, where the question stops being whether an agent can call a tool and becomes whether that call can be identified, scoped and logged.

## Governance: a governed MCP server

**What it shows.** Connecting an agent to sensitive data is easy. The interesting part is the boundary: who may the agent ask, what may it do, how many times, and where is the proof of what happened. This server exposes Kubernetes cost data from OpenCost to an agent under three constraints that live in code rather than in a prompt: read-only by construction, one audit line per call, and a budget guard.

Least privilege appears twice, in two different places, and that is deliberate. It is **declared** in the protocol metadata, through MCP annotations a host reads before ever calling the tool, and **enforced** in the policy module at call time. Without the annotations, MCP's defaults advertise the opposite. And the architecture itself is checked rather than described: one of the thirty tests fails if the business logic ever imports the protocol or the governance layer.

Its most useful feature is a deliberate limitation. The budget guard counts in memory, so it cannot see other instances. That is not a bug, and the section below explains why it became more interesting than the parts that work.

**What it needs.** Python. Runs fully offline in synthetic mode, with fictional data. No cluster required. Point it at a real OpenCost when you have one.

→ [model-context-protocol](https://github.com/christian-dussol-ai-native/model-context-protocol)

📄 The writing behind it: AAIF Project Focus

### What I learned

The protocol carries less than I expected, and that turns out to be the good news. MCP standardises how a tool is described and called, and deliberately leaves policy, identity and audit to the surrounding system. That is what makes it composable: the governance I needed was mine to write, not something I had to fight the protocol to add.

The synthetic mode changed who can run this. A governed server that needs a live cluster and a cost backend is a demo three people will try. One that runs offline with fictional data is something a reader can have working in five minutes, and the governance is identical either way.

Read-only by construction beats read-only by instruction. A boundary that lives in the code survives a prompt that does not, and the difference matters most on the day someone finds a way to phrase the request differently.

Keeping governance behind a swappable interface mattered more than the implementation behind it. Today the rules are Python. Tomorrow a Kyverno or OPA engine could replace them without touching the service or the protocol layer. The policy engine is an implementation detail; the fact that a decision happens before the data is read is not.

And the limitation taught me the most. The budget counter is process-local, so behind a load balancer with several instances the effective limit becomes a multiple of the configured one. Before the July 2026 stateless revision, a remote server could lean on sticky sessions, so a client kept returning to the same instance and the per-process counter held together by accident. With any request now free to reach any instance, that counter stops being a footnote and becomes a visible gap. **The revision did not create the limitation and does not fix it. It removed what used to mask it.**

## Policy: three composable Skills for Kyverno governance

**What it shows.** A generator that turns natural language into a policy, its Chainsaw tests and its pass and block fixtures, always defaulting to Audit mode. An auditor that scores a policy across eight dimensions and calls the generator when tests are missing. And a FinOps Skill that queries live OpenCost data through MCP, generates tiered limits from actual usage, then invokes the other two to test and validate its own output.

The observable moment is a file shipped on purpose: `bad-policy.yaml`, generic LLM output, scores 1 out of 8. Run the auditor on it and watch it name the production issues hidden in YAML that looked correct: enforce by default, Deployment instead of Pod so autogen misses StatefulSet and CronJob, `"*"` instead of `"?*"`, no annotations, no tests.

A Skill does not make the model smarter. It makes it disciplined.

**What it needs.** Claude Code and Python. The full FinOps loop adds Minikube and OpenCost, with setup scripts included.

→ [kyverno/skills](https://github.com/christian-dussol-cloud-native/kyverno/tree/main/skills)

📄 The writing behind it: [From Prompts to Packages](../ai-native/skills-series/)

### What I learned

Composition works, and it is the part I would not have predicted. The FinOps Skill pulls real usage, generates limits, then calls the generator to produce tests and the auditor to score its own output. Three Skills validating each other with nobody orchestrating them by hand. That is closer to a system than to a set of prompts.

Encoding expertise turned out to be more durable than I expected. The generator is not a better prompt, it is a workflow with validation passes, official policy references and mandatory tests. Once written, it produces the same quality on a Tuesday afternoon as it did the day I built it, which is not true of me.

The same prompt across several tools produced YAML that looked correct and carried seven production issues. Enforce by default, so one apply can cause an outage. Matching Deployment rather than Pod, so autogen never covers StatefulSet, DaemonSet, Job or CronJob. `"*"` instead of `"?*"`, which allows the empty value the rule exists to forbid. And no test at all.

Every guard rail in these Skills exists because I hit the wall it prevents. That is the difference between encoding expertise and prompting for it: the discipline comes from what went wrong before, and a model cannot supply what it has not lived.
