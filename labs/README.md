---
description: >-
  Reproducible labs behind the writing, from GPU allocation to governed MCP
  servers. Most run locally, no GPU and no cloud account required.
---

# Labs

The article is the explanation. The repository is the proof. This page is the proof.

Each lab exists to answer a question I could not answer by reading. They are not installation tutorials, and they are not demos of a happy path. Every one of them is built to make a specific mechanism observable: what the scheduler decides, what the policy refuses, what the audit trail records.

## The argument that runs through all of them

Governance conditions measurement. Not the other way round.

The same pattern appears in nine of these ten labs, and it was not planned. Kyverno sits at admission, and without it the layer above produces nothing worth having. Metrics from pods with no limits are meaningless. Traces from services with no instrumentation annotation are absent. Costs with no allocation labels cannot be attributed. A resize with no ceiling is an unbounded write to your bill. A policy with no test is a guess in YAML.

That constraint is not a compliance overhead bolted on afterwards. It is what makes the data downstream mean anything.

## Reproducible on purpose

The expensive parts of this stack are easy to write about and hard to verify. Most people reading about GPU allocation or inference routing do not have a GPU cluster to test the claim on, so they have to take the author's word for it.

Most of these labs remove that. Simulated GPUs, a vLLM simulator, synthetic cost data: the scheduling, the routing and the policy decisions are real even when the hardware is not. You are not asked to trust the write-up. You can watch the mechanism, break it, and disagree with me from evidence.

That constraint also shapes what they can teach. Without hardware they cannot demonstrate throughput. What they demonstrate is **behaviour**, which is the part that survives the next hardware generation anyway.

Where a lab needs a cloud account or a specific cluster version, it says so.

## In this section

[**Infrastructure foundations**](infrastructure-foundations.md). Serverless economics with Knative, a universal control plane with Crossplane, eBPF networking and PCI-DSS segmentation with Cilium.

[**Observability**](observability.md). Cost attribution with Prometheus, and a unified telemetry pipeline with OpenTelemetry. Both make the same point: what you can observe is decided at admission.

[**The AI substrate**](the-ai-substrate.md). GPU tier fallback with DRA, and model-aware inference routing with GAIE. Simulated hardware, real scheduling decisions.

[**The agentic layer**](the-agentic-layer.md). A governed MCP server exposing cost data under least privilege, and three composable Kyverno Skills.

[**Kubernetes operations**](kubernetes-operations.md). In-place pod resize, and the guardrails that have to exist before you enable it.

All of it is open source under CC BY-SA 4.0.
