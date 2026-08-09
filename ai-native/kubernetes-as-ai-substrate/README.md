---
description: >-
  Four floors, one stack. How Kubernetes is becoming the substrate for AI:
  allocation, serving, routing, governance, and the token that prices all of it.
---

# Kubernetes as AI Substrate

## Four floors, one stack

A platform offers features you opt into. A substrate is the ground everything stands on, supporting without imposing.

Kubernetes is not adding AI features on the side. It is reshaping itself, one primitive at a time, into the thing the AI stack runs on natively. Accelerator allocation, distributed inference, intelligent routing, agent identity: capabilities that used to live in separate tools, pulled one by one into the control plane.

This series climbs that stack from the hardware up. Each piece explores one floor and points at the next. Together they trace a single move, repeated at every level: **Kubernetes shifting from counting to reasoning.**

I write it from a specific seat, a regulated financial-services end user, where deploying the model is the easy part and operating it under constraints is the real work. From that seat the same two questions return at every floor: _what does this cost, and how do I audit it._

The series is partial by design. The building is still going up.

### The series, bottom to top

#### 1. [Allocation: Dynamic Resource Allocation](allocation-dra.md)

For a decade Kubernetes counted accelerators. Counting cannot express preference, tier, or topology. DRA replaces the counter with a model.

#### 2. [Serving: llm-d](serving-llm-d.md)

A GPU is not a served model. Prefill and decode share almost nothing, and running them on the same GPU wastes both.

#### 3. [Routing: the Gateway API Inference Extension](routing-gateway-api-inference-extension.md)

Once a model is served across many pods, a request has to reach the right one. The instinct is a load balancer. For inference, that instinct is wrong.

#### 4. [Governance: One Stack, Two Foundations](one-stack-two-foundations.md)

The CNCF and the Agentic AI Foundation are shaping the agentic floor in parallel. They are not competing, and they are no longer separate movements.

#### 5. [The Economic Layer: The Meter and the Machine](the-meter-and-the-machine.md)

The token became the atomic unit of AI value. But you cannot govern the cost of tokens if you do not understand the machine that produces them.

#### 6. [The Shape I See](the-shape-i-see.md)

The capstone. Standing still, pointing back down the slope, and naming the ridge above before the climb continues.

***

**The builds behind these pieces:** [dynamic-resource-allocation](https://github.com/christian-dussol-ai-native/dynamic-resource-allocation) · [gateway-api-inference-extension](https://github.com/christian-dussol-ai-native/gateway-api-inference-extension)
