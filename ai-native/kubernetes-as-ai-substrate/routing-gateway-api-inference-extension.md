---
description: >-
  Inference backends are not interchangeable. Each pod carries its own cache,
  queue and load. Routing has to read live state, not spread traffic blindly.
---

# Routing: Gateway API Inference Extension

## Why Your Load Balancer Doesn't Understand AI Traffic

<figure><img src="../../.gitbook/assets/LinkedIn Cover.png" alt=""><figcaption></figcaption></figure>

### The routing floor: sending each request to the right pod.

Once a model is served across many pods, a request has to reach one of them. The instinct is a load balancer.

For inference, that instinct is wrong. Load balancing assumes the backends are interchangeable, and inference backends are not. Each pod carries its own KV cache, its own queue depth, its own load. And a one-token prompt is not the same workload as a long-context request, so treating them as equivalent units of traffic is a category error before it is a performance problem.

The Gateway API Inference Extension adds a per-request scheduler to the gateway, one that reads live pod state and places each request where it will actually run best. **It does not spread traffic. It routes with intent.**

### What the article covers

* Why round-robin and least-connections fail on inference traffic, concretely
* The KV cache: the reusable state a model builds while reading a prompt, and why reusing it means the expensive prefill stops being recomputed
* The per-request scheduler, and what live pod state it reads to make a placement decision
* How priority becomes declarative: under contention, an explicit object decides that production traffic is served before sandbox work, as config rather than buried in code

### Read

* **Medium article**: [Why Your Load Balancer Doesn't Understand AI Traffic (and What Fixes It)](https://medium.com/@christian.dussol/why-your-load-balancer-doesnt-understand-ai-traffic-and-what-fixes-it-f446e8a3e3c1)
* **LinkedIn Pulse**: [Why Your Load Balancer Doesn't Understand AI Traffic](https://www.linkedin.com/pulse/why-your-load-balancer-doesnt-understand-ai-traffic-what-dussol-1njxe/)
* **GitHub**: [gateway-api-inference-extension](https://github.com/christian-dussol-ai-native/gateway-api-inference-extension)
