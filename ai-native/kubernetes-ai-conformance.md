---
description: >-
  The CNCF program that ends the fragmentation of AI on Kubernetes. DRA, gang
  scheduling, inference routing, and what portability means for sovereignty.
---

# Kubernetes AI Conformance

## The end of the AI infrastructure wild west

Every vendor had approached AI on Kubernetes differently. Proprietary GPU scheduling, incompatible allocation models, platform-specific monitoring. A workload built on one platform needed a rewrite to run on another. Eighty-two percent of organizations are building custom AI solutions and fifty-eight percent run them on Kubernetes, which made the fragmentation expensive rather than merely annoying.

In November 2025 the CNCF launched the Certified Kubernetes AI Conformance Program. This is a technical deep-dive into what it actually requires, and what it changes for platform teams.

### What the article covers

* **The fragmentation problem, concretely.** A distributed training job needs eight GPUs. Six get allocated, two do not. The job cannot proceed and the six GPUs are locked. That deadlock is why teams over-provision by forty to fifty percent
* **Dynamic Resource Allocation.** GPUs claimed the way PersistentVolumeClaims work, with flexible sharing, fine-grained memory allocation, and no vendor-specific configuration
* **All-or-nothing scheduling.** Kueue and Volcano, and why gang scheduling is the difference between a training job that runs and eight GPUs sitting idle behind a partial allocation
* **Gateway API inference extension.** Model-aware routing, header-based selection for OpenAI-compatible APIs, and traffic splitting for A/B testing new model versions
* **Standardized monitoring.** GPU utilization, memory, temperature, power, inference latency, queue depth. A Grafana dashboard that works on any conformant platform without a rewrite
* **The FinOps consequence.** Portable cost models. You can finally compare platforms on the same terms, and chargeback stops being a bespoke engineering project
* **The European angle.** Kubermatic, SUSE, Gardener and Giant Swarm certified in v1.0. Portability is the foundation of digital sovereignty, and for regulated industries that is not an abstract point

### Read

* **Medium article**: [Kubernetes AI Conformance: Technical Deep-Dive and Strategic Implications](https://medium.com/@christian.dussol/kubernetes-ai-conformance-technical-deep-dive-strategic-implications-e6748e281ad1)
