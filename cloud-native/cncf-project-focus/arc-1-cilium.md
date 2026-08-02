---
description: >-
  eBPF rewrote the Kubernetes networking layer. Cilium as the reference
  implementation: kube-proxy replacement, kernel-speed policy, and the iptables
  confusion.
---

# Episode 3: Cilium

**Kernel-Native Kubernetes Networking.**

eBPF is the technology that quietly rewrote the Kubernetes networking layer. This episode dissects Cilium as the reference implementation: what it replaces, what it enables and the common misconception about where iptables actually lives.

<figure><img src="https://3864580007-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F782Y46kG3IDKMjaaCmCh%2Fuploads%2FivKawqCpqvhbyVZNeFPY%2F1.png?alt=media&#x26;token=bb3af912-4707-49f9-aee7-b32ab9221922" alt="" width="563"><figcaption></figcaption></figure>

### 📎Visual companion

[CNCF Project Focus #3: Cilium carousel (PDF)](https://github.com/christian-dussol-cloud-native/cilium/blob/main/carousel/CNCF%20Project%20Focus%20%233%20-%20Cilium.pdf)

### What the episode covers

* eBPF fundamentals without the marketing gloss
* kube-proxy replacement and why that matters at scale
* Network policy enforcement at kernel speed
* The iptables confusion: userspace configuration vs. kernel execution

### Read the deep-dive

* **Medium article** (published in AWS in Plain English): [Cilium — Eliminating the hidden network overhead in Kubernetes](https://aws.plainenglish.io/cilium-eliminating-the-hidden-network-overhead-in-kubernetes-cfa6ac10d084)
* **GitHub lab**: [github.com/christian-dussol-cloud-native/cilium](https://github.com/christian-dussol-cloud-native/cilium)
* **Runnable lab**: [Networking: eBPF, policy and observability](../../labs/infrastructure-foundations.md)
