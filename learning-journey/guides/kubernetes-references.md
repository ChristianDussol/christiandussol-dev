---
description: >-
  The Kubernetes Enterprise Learning Series and the references it produced. A
  cheat sheet organized by role, and a resource management guide built from
  production mistakes.
---

# Kubernetes References

## The parts I kept getting wrong

Kubernetes documentation is exhaustive, which is its problem. These references are the opposite: short, opinionated, and built from the things I had to learn twice.

They came out of a deliberate learning project rather than a note-taking habit, and the article below explains that project before the references make sense.

***

### The series that produced them

[**Kubernetes Enterprise Learning Series: A Practical Guide to Production-Ready Implementations**](https://medium.com/@christian.dussol/kubernetes-enterprise-learning-series-a-practical-guide-to-production-ready-implementations-313ae521028b)

The gap between _knowing_ Kubernetes and _running it in production_ is wide, and most tutorials do not close it. They teach you to deploy hello-world. They do not prepare you for zero-downtime operations, resource governance, or the cost conversation you will eventually have with finance.

This is the arc-opener for a three-part series I built to close that gap for myself, structured explicitly around Scott Young's UltraLearning method:

* **Directness.** Real projects from day one, no toy examples
* **Drilling.** Isolate the weak points and attack them specifically
* **Feedback.** Deploy it, monitor it, watch it break, fix it
* **Retrieval.** Practice without the docs open
* **Building over consuming.** Deploy, test, break, learn, repeat

The three parts build on each other: master the operations, then the governance, then the advanced features that are only safe once the governance exists. The full series lives under Cloud Native → Kubernetes.

***

### Kubernetes Cheat Sheet

The commands and manifests I actually reach for. Not the exhaustive list, the working one.

→ [GitHub: k8s-cheatsheet.md](https://github.com/christian-dussol-cloud-native/kubernetes/blob/main/guides/k8s-cheatsheet.md)

### Kubernetes Resource Management

Requests, limits, QoS classes, and why memory limits behave differently from CPU limits.

CPU is compressible: exceed the limit and the container is throttled. Memory is not: exceed it and the container is killed. That asymmetry is the single most common source of production surprises I have seen, and it is buried three levels deep in the official docs.

This guide covers what to set, what happens when you get it wrong, and how QoS classes decide who gets evicted first when a node runs out.

→ [GitHub: k8s-resources-management.md](https://github.com/christian-dussol-cloud-native/kubernetes/blob/main/guides/k8s-resources-management.md)
