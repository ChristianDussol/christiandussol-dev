---
description: >-
  GPU tier fallback and model-aware inference routing, both runnable on a
  laptop. Simulated hardware, real scheduling and routing decisions.
---

# The AI substrate

Two floors of the AI substrate, made observable without hardware. The accelerators are simulated and the model server is a stand-in, but the scheduling and the routing decisions are real. That is the line these labs are careful to draw.

## Allocation: walking the Prioritized List cascade with DRA

**What it shows.** Three mock GPU tiers (H100, A100, L4) and a claim that says `firstAvailable`. Then a script that makes the top tier unavailable and lets you watch the scheduler descend: H100 gone, the pod lands on A100; A100 gone, it lands on L4. Declarative hardware heterogeneity, observed rather than described.

It runs on Kind with the SIG Node example driver, so the GPUs are simulated. The tutorial says so plainly: the scheduling and allocation are real, no CUDA workload runs. Swap in NVIDIA's driver in production and the manifests do not change, which is the whole point of a standard primitive.

**What it needs.** Kind, Docker, about 4 GB of RAM and thirty minutes. No GPU, no cloud, no cost.

→ [dra-prioritized-list-tutorial](https://github.com/christian-dussol-ai-native/dynamic-resource-allocation/tree/main/dra-prioritized-list-tutorial)

📄 The writing behind it: [Allocation: DRA](../ai-native/kubernetes-as-ai-substrate/allocation-dra.md)

## Routing: model-aware inference routing with GAIE and agentgateway

**What it shows.** The three GAIE primitives wired together on Kind: an InferencePool grouping model servers, an Endpoint Picker the Gateway consults over ext-proc before every request, and an InferenceObjective declaring which workload wins when capacity is contended. A vLLM simulator stands in for a model server, so none of it needs a GPU.

The moment that lands is the response header. `x-inference-pod` names the exact pod the Endpoint Picker chose, so the routing decision stops being a claim you read and becomes something you can point at.

The InferenceObjective is the part worth dwelling on from a regulated seat. Priority between tenants expressed as a reviewable Kubernetes object rather than buried in code, which is the inference-layer echo of DRA's prioritized list.

**What it needs.** Kind, cloud-provider-kind, Helm and curl. No GPU, no cloud.

→ [gateway-api-inference-extension](https://github.com/christian-dussol-ai-native/gateway-api-inference-extension)

📄 The writing behind it: [Routing: Gateway API Inference Extension](../ai-native/kubernetes-as-ai-substrate/routing-gateway-api-inference-extension.md)
