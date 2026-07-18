---
description: >-
  Resizing CPU and memory on a running container without a restart. What the
  feature enables, and the governance it needs before production.
---

# In-Place Pod Resize

## Vertical scaling without the restart.

Changing a container's CPU or memory used to mean restarting it. That is fine until the workload holds state, or until the restart lands in the middle of something that matters.

In-place pod resize removes that constraint. It is a genuinely useful capability, and it is also the kind of capability that can quietly cost you a lot of money or take down a node if nothing is watching. The interesting part is not the feature. It is the guardrails.

📎 **Visual companion**: [In-Place Pod Resize carousel (PDF)](https://github.com/christian-dussol-cloud-native/kubernetes/blob/main/carousel/InPlace-PodResize.pdf)

### What this covers

* **The `resizePolicy` field**, and why CPU and memory behave differently. CPU can usually change with `restartPolicy: NotRequired`. Memory often cannot, because shrinking it under a running process is how you get an OOM kill
* **Where it fits in the scaling picture.** HPA adds pods. Cluster Autoscaler adds nodes. Vertical resize changes what a pod has. A memory leak is not fixed by more replicas, and a CPU-bound task is not fixed by a bigger node
* **The governance requirement.** LimitRange caps how large a resize can go. ResourceQuota stops the cumulative creep. Kyverno validates the ratio on every resize operation. Without them, a resize is an unbounded write to your cloud bill
* **The hands-on demo.** A working cluster setup with the governance applied first, then the resize operations, so you can watch the guardrails hold

### Read

* **Medium article**: [Kubernetes 1.33: How In-Place Pod Resize Brings Significant Improvement to Vertical Scaling](https://medium.com/@christian.dussol/kubernetes-1-33-how-in-place-pod-resize-brings-significant-improvement-to-vertical-scaling-7a2da0380b7d)
* **Hands-on demo and tutorial**: [k8s-pod-resize-demo](https://github.com/christian-dussol-cloud-native/kubernetes/tree/main/demo-features/1.33/k8s-pod-resize-demo)
