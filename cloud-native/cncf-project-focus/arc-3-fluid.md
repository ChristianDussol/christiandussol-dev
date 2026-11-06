---
description: >-
  Fluid, dataset orchestration and caching on Kubernetes: who needs a cache,
  four ways to feed a pod, the mechanism, and what Fluid does not do.
---

# Episode 8: Fluid

**Dataset orchestration and caching on Kubernetes.**

The arc's second question: how do workloads get their data?

A Job copies 443.5 MiB of files from a remote Apache mirror. The first read takes just over a minute, because every byte travels from remote storage. Without a shared cache, every new pod, every replica and every epoch pays that cost again.

The China Merchants Bank case study puts it in one line: "when data is not ready, allocated accelerators wait." Once the GPU is shared, a GPU waiting on data is the next thing being wasted.

<figure><img src="../../.gitbook/assets/CNCF Project Focus - Fluid.png" alt=""><figcaption></figcaption></figure>

### 📎 Visual companion

[CNCF Project Focus #8: Fluid carousel (PDF)](https://github.com/christian-dussol-cloud-native/fluid/blob/main/carousel/CNCF%20Project%20Focus%20%238%20-%20Fluid.pdf)

### What the episode covers

* **Who needs a cache.** Training datasets, re-read every epoch. Model weights, loaded by every new replica. Checkpoints, read back to evaluate and deploy. Data read once is the case where it depends, because it stays cold unless something preloads it
* **The four ways to feed a pod.** A direct PVC, where every read is remote. An init container that copies the data first. A shared cache you run and operate yourself. And Fluid, which is a cache engine orchestrated by Kubernetes
* **What Fluid is, in its own words.** "Fluid is an open source Kubernetes-native Distributed Dataset Orchestrator and Accelerator for data-intensive applications, such as big data and AI applications." First commit in July 2020, CNCF Sandbox in April 2021, Incubating since January 2026
* **What it turns into Kubernetes objects.** Fluid does not replace your storage. It takes a cache engine, Alluxio or JuiceFS among others, and makes it declarable: DECLARE where the data is, CACHE a copy close by, PRELOAD it before the pod starts, PLACE the pod next to it
* **And what it does not do.** It is not a storage system, and not a cache engine itself. The first read stays cold unless the data is preloaded. The cache is bounded, 4 GiB in the tutorials. And acceleration depends on the runtime, because not every runtime caches

### Run it yourself

Four official tutorials, in the order the episode follows them. Quick Start installs Fluid on a cluster. Accelerate Data Accessing (POSIX) reads the same data twice. Data Preloading warms the cache before the pod starts. Cache Co-locality runs the pod next to its cache. The timings in the carousel come from those tutorials, with the caveat the documentation itself states: they depend on your network environment.

→ [fluid-cloudnative.github.io/docs](https://fluid-cloudnative.github.io/docs) · [GitHub repository](https://github.com/christian-dussol-cloud-native/fluid)
