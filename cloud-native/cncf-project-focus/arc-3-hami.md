---
description: >-
  HAMi, heterogeneous GPU sharing on Kubernetes: who needs a slice of a GPU, the
  three ways to share one, four components, and the experimental DRA path.
---

# Episode 7: HAMi

**Heterogeneous GPU sharing on Kubernetes.**

Arc 3 asks three questions in order. HAMi answers the first: how do workloads share a GPU?

Kubernetes counts `nvidia.com/gpu` as whole devices. A pod that needs 4000 MiB still gets the entire card, and ten pods with that same small request lock ten GPUs. You pay for ten cards, and your workloads use a fraction of the memory on them.

<figure><img src="../../.gitbook/assets/CNCF Project Focus - HAMi.png" alt=""><figcaption></figcaption></figure>

### 📎 Visual companion

[CNCF Project Focus #7: HAMi carousel (PDF)](https://github.com/christian-dussol-cloud-native/hami/blob/main/carousel/CNCF%20Project%20Focus%20%237%20-%20HAMi.pdf)

### What the episode covers

* **Who actually needs a slice.** Small-model inference, notebooks, dev and CI are a good fit. Large-model serving depends, since vLLM targets 90% of GPU memory by default and wants sizing before sharing. Large-model training is a poor fit: a job that keeps every compute unit busy gains nothing from being split
* **The three ways to share, and what each one gives up.** Time-slicing lets pods take turns, and nothing stops one of them from using all the memory. MIG splits the card physically, on selected NVIDIA data-center GPUs only. Software partitioning enforces memory and compute limits from a library inside the container, and leaves cache and memory bandwidth unpartitioned
* **What HAMi is.** Heterogeneous AI computing virtualization middleware: an open source platform for managing heterogeneous AI computing devices in Kubernetes clusters, which lets several containers and workloads share a device. CNCF Sandbox in August 2024, Incubating since July 2026, with v2.9.0 used in this episode's labs
* **Four components, one per layer.** A mutating webhook at admission, a scheduler extender in the control plane, a device plugin on the node, and HAMi-core loaded inside the container
* **The mechanism in four steps.** EXPOSE, SHARE, LIMIT, MEASURE. Each physical GPU is registered as ten schedulable slots by default. Two pods with the same `nvidia.com/gpumem` request land on the same card. And `nvidia-smi` inside the container reports the ceiling it was given rather than the 15360 MiB the card actually has
* **The DRA path, marked experimental.** The same slice requested through a `ResourceClaim` instead. DRA replaces the scheduling path, and HAMi-core still enforces the limits in the container

### Run it yourself

The episode points at the official HAMi labs rather than at a lab of my own, and every output in the carousel carries the lab it came from. Lab 2 runs on a laptop with a fake GPU and no hardware. Labs 1 and 3 need one cloud VM with a T4. Lab 4 covers the DRA path, on Kubernetes 1.34 or later with the `DRAConsumableCapacity` feature gate.

→ [project-hami.io/tutorials](https://project-hami.io/tutorials) · [GitHub repository](https://github.com/christian-dussol-cloud-native/hami)
