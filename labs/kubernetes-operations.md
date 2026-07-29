---
description: >-
  Vertical scaling without the restart, and the guardrails that have to exist
  before the feature is safe to enable.
---

# Kubernetes operations

Operational primitives where the feature is simple and the governance is the content.

### Resize: vertical scaling without the restart

**What it shows.** CPU changed live on a running pod, 0.5 to 1.5 and back down to 0.3, with zero restarts throughout. Then the part that matters more: quotas, LimitRanges and Kyverno refusing a resize that would have gone too far, and new namespaces getting their quota generated automatically.

The README states the risk plainly rather than selling the feature. Anyone with permission on the resize subresource can starve a cluster, so the demo deploys the guardrails first and the resize second.

**What it needs.** A cluster running Kubernetes 1.33 or later with containerd, plus Kyverno.

_Last validated against Kubernetes 1.33. The feature has evolved since; treat the lab as a snapshot of that release._

→ [k8s-pod-resize-demo](https://github.com/christian-dussol-cloud-native/kubernetes/tree/main/demo-features/1.33/k8s-pod-resize-demo)

📄 The writing behind it: In-Place Pod Resize

#### What I learned

Watching CPU change on a running pod with the restart counter staying at zero is genuinely satisfying, and it closes a real gap. Right-sizing used to mean choosing between a bad estimate kept forever and a restart nobody wanted to schedule. Now the estimate can be wrong and corrected, which lowers the cost of getting it wrong in the first place.

It also completes the scaling picture rather than competing with it. HPA adds pods, Cluster Autoscaler adds nodes, and vertical resize finally changes what a single pod has. A memory leak was never a replica problem, and until this existed there was no honest answer to it.

The governance turned out to be simpler than expected: LimitRange, ResourceQuota and Kyverno already knew how to cap this. No new mechanism, just the existing controls pointed at a new verb.

Resize is a subresource, which means permission to resize is permission to consume. RBAC on `pods/resize` deserves as much attention as the LimitRange that caps the value, and it is the control most likely to be forgotten because the feature looks like a convenience rather than a privilege.

Deploying the guardrails before the demo was not presentation order. It was the only safe order.
