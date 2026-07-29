---
description: >-
  A governed MCP server and three composable Kyverno Skills. Where the boundary
  lives in auditable infrastructure rather than in a prompt you hope holds.
---

# The agentic layer

The top floor, where the question stops being whether an agent can call a tool and becomes whether that call can be identified, scoped and logged.

## Governance: a governed MCP server

**What it shows.** Connecting an agent to sensitive data is easy. The interesting part is the boundary: who may the agent ask, what may it do, how many times, and where is the proof of what happened. This server exposes Kubernetes cost data from OpenCost to an agent under three constraints that live in code rather than in a prompt: read-only by construction, one audit line per call, and a budget guard.

Its most useful feature is a deliberate limitation. The budget guard counts in memory, so it cannot see other instances. That is not a bug: it marks exactly where the server stops and the platform begins.

**What it needs.** Python. Runs fully offline in synthetic mode, with fictional data. No cluster required. Point it at a real OpenCost when you have one.

→ [model-context-protocol](https://github.com/christian-dussol-ai-native/model-context-protocol)

📄 The writing behind it: [AAIF Project Focus](../ai-native/aaif-project-focus.md)

## Policy: three composable Skills for Kyverno governance

**What it shows.** A generator that turns natural language into a policy, its Chainsaw tests and its pass and block fixtures, always defaulting to Audit mode. An auditor that scores a policy across eight dimensions and calls the generator when tests are missing. And a FinOps Skill that queries live OpenCost data through MCP, generates tiered limits from actual usage, then invokes the other two to test and validate its own output.

The observable moment is a file shipped on purpose: `bad-policy.yaml`, generic LLM output, scores 1 out of 8. Run the auditor on it and watch it name the production issues hidden in YAML that looked correct: enforce by default, Deployment instead of Pod so autogen misses StatefulSet and CronJob, `"*"` instead of `"?*"`, no annotations, no tests.

A Skill does not make the model smarter. It makes it disciplined.

**What it needs.** Claude Code and Python. The full FinOps loop adds Minikube and OpenCost, with setup scripts included.

→ [kyverno/skills](https://github.com/christian-dussol-cloud-native/kyverno/tree/main/skills)

📄 The writing behind it: [From Prompts to Packages](../ai-native/skills-series/)
