---
description: >-
  Prefill is compute-bound, decode is memory-bound. Understanding llm-d, then
  exploring the architecture without owning a GPU cluster.
---

# Serving: llm-d

**From GPU allocation to distributed inference, and what you can explore before you have the hardware.**

DRA gets you the hardware. It does not get you a served model.

This floor comes in two parts, written three months apart. The first reads the architecture. The second answers the question the first one left open.

### Part one: understanding llm-d

Serving a large language model splits into two phases that share almost nothing. **Prefill** reads the prompt and is compute-bound. **Decode** generates tokens and is memory-bound. Run them on the same GPU and they interfere with each other, and the hardware is never fully used for either.

llm-d makes prefill and decode disaggregation a first-class pattern: separate pools, scaled independently, orchestrated above vLLM rather than replacing it. It is a control plane for distributed inference, not an engine.

**DRA gives you the hardware. llm-d makes it a service.**

What the piece covers: the prefill and decode split and why the two phases have opposite resource profiles, what disaggregation buys and what it costs in operational complexity, where llm-d sits relative to vLLM, and why separate pools make inference economics legible one floor up.

It closes on what I had not done. I had read the architecture and the code, but I had not run it at scale, because the realistic case needs multi-GPU infrastructure. That left a question: **what can you learn about the architecture before you have the hardware?**

→ **Read it**: [Medium](https://medium.com/@christian.dussol/from-gpu-allocation-to-distributed-inference-understanding-llm-d-concept-brief-42cffc4cb946) · [LinkedIn Pulse](https://www.linkedin.com/pulse/from-gpu-allocation-distributed-inference-llm-d-concept-dussol-7wcye/)

### Part two: exploring it without a GPU cluster

The answer turned out to be neither everything nor nothing, and the interesting part is the line between the two.

* **Why the question is not about money.** Renting bills by the hour while you read the documentation and mistype a flag. Buying commits you before you know what you need. Neither route answers what I actually had, which was not what it costs but **which configuration I would want to validate**
* **Calculating and simulating are not two levels of precision.** An analytical calculation answers how long one pass through the model takes. A simulator answers how a cluster behaves under real traffic: requests arriving when they arrive, waiting in a queue, being grouped into batches. None of that is in the first calculation, and all of it decides what your users experience
* **The number that makes the case.** Two BLIS runs, identical except for one flag. The analytical model reported 18,427 tokens per second across the cluster, the calibrated one 10,631. Sizing a fleet on the first would over-estimate capacity by a factor of about 1.7. **That is not a rounding difference. That is a purchase order.** Both runs take seconds
* **What the tool says it does not model**, read before getting attached to any number. Roughly 7% median error, but only against a named list of models on H100, A100 and L40S. Outside that set the error is not known, and nobody has measured it. The network is not simulated at all, and the calibration does not cover deeply saturated regimes
* **Two ways to split a model, two different questions.** Tensor parallelism asks what to do when the model is too big. Data parallelism asks what to do when the queue is too long. The second is the one a simulator can help you reason about without owning a cluster

A simulator does not remove the need for hardware. **It changes what you need the hardware for.** The expensive hours stop being spent finding out what you should have asked, and start being spent checking the two or three answers that survived a hundred runs on a laptop.

→ **Read it**: [Medium](https://medium.com/@christian.dussol/exploring-inference-architecture-without-a-gpu-cluster-concept-brief-49786a876fe9) · [LinkedIn Pulse](https://www.linkedin.com/pulse/exploring-inference-architecture-without-gpu-cluster-concept-dussol-t1w4e/)

→ **Run it**: [Serving: what a simulator lets you learn without a GPU](../../labs/the-ai-substrate.md) in Labs

***

_Simulating is not reproducing the hardware. It is building a model useful enough to answer some questions, and knowing precisely which ones stay out of reach._
