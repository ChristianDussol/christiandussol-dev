---
description: >-
  Kubernetes counted GPUs for a decade. DRA replaces the counter with a model,
  so the cluster reasons about hardware instead of tallying it.
---

# From Counting GPUs to Reasoning About Them

<figure><img src="https://3864580007-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F782Y46kG3IDKMjaaCmCh%2Fuploads%2FetS4Tg8DoUdV1Ug9wgnL%2F1.png?alt=media&#x26;token=deb6b09c-90cb-4cd7-b585-4596118bdc9c" alt="" width="563"><figcaption></figcaption></figure>

## The allocation floor: getting the right hardware to the right workload.

For a decade, Kubernetes counted accelerators. You asked for one GPU, the scheduler found a free one, and that worked for as long as every node looked the same.

It broke the moment clusters started mixing H100s, A100s and L4s. Counting cannot express preference. It cannot express tier, or topology, or "I would like an H100 but I will take an A100 and I can live with an L4."

Dynamic Resource Allocation replaces the counter with a model. A workload describes what it needs, the way a PersistentVolumeClaim describes storage, and Kubernetes reasons about which device actually fits. **The cluster stops counting hardware and starts reasoning about it.**

This is the first floor of the substrate, and the piece where the whole series began.

## What the article covers

* The limits of the device-plugin counting model, and where they show up in a mixed-accelerator cluster
* How DRA claims work, and why the PersistentVolumeClaim analogy is the right mental model rather than a convenient one
* Prioritized lists: expressing preference and fallback rather than a single hard requirement
* What this makes possible one floor up, and why the substrate framing was already visible from here

## Read

* **Medium article**: [From Counting GPUs to Reasoning About Them: How Kubernetes DRA Powers AI-Native Infrastructure](https://medium.com/@christian.dussol/from-counting-gpus-to-reasoning-about-them-how-kubernetes-dra-powers-ai-native-infrastructure-369cc75a667e)
* **GitHub**: [dynamic-resource-allocation](https://github.com/christian-dussol-ai-native/dynamic-resource-allocation)
* **Runnable lab**: [Walking the Prioritized List cascade](../../labs/the-ai-substrate.md)
