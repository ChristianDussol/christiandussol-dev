---
description: >-
  A GPU is not a served model. Prefill is compute-bound, decode is memory-bound,
  and llm-d makes their disaggregation a first-class pattern.
---

# Serving: llm-d

## From GPU Allocation to Distributed Inference: Understanding llm-d

DRA gets you the hardware. It does not get you a served model.

Serving a large language model splits into two phases that share almost nothing. **Prefill** reads the prompt and is compute-bound. **Decode** generates tokens and is memory-bound. Run them on the same GPU and they interfere with each other, and the hardware is never fully used for either.

llm-d makes prefill and decode disaggregation a first-class pattern: separate pools, scaled independently, orchestrated above vLLM rather than replacing it. It is a control plane for distributed inference, not an engine.

**DRA gives you the hardware. llm-d makes it a service.**

### What the article covers

* The prefill and decode split, and why the two phases have opposite resource profiles
* What disaggregation buys you, and what it costs in operational complexity
* Where llm-d sits relative to vLLM: a control plane above the engine, not a competitor to it
* Why separate pools make inference economics legible, which turns out to matter one floor up

### Read

* **Medium article**: [From GPU Allocation to Distributed Inference: Understanding llm-d (Concept Brief)](https://medium.com/@christian.dussol/from-gpu-allocation-to-distributed-inference-understanding-llm-d-concept-brief-42cffc4cb946)
* **LinkedIn Pulse**: [From GPU Allocation to Distributed Inference](https://www.linkedin.com/pulse/from-gpu-allocation-distributed-inference-llm-d-concept-dussol-7wcye/)
