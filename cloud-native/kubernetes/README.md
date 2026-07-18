---
description: >-
  Kubernetes operations from production experience: command workflows organized
  by role, resource governance, and in-place pod resize with the guardrails it
  needs.
---

# Kubernetes

The substrate under everything else on this site. These are the parts I had to learn twice.

Each topic below started the same way: something broke, or something was slower than it should have been, and the official documentation explained the mechanism without explaining the choice. What follows is the version I wish had existed at the time.

### In this section

#### [Command Reference](command-reference.md)

Organizing kubectl by role rather than alphabetically. Developer, administrator, security, troubleshooting, monitoring. Speed in Kubernetes is not about knowing every command, it is about having the right ones at hand for the moment you are in.

#### [Resource Management](resource-management.md)

Pod resources, LimitRange, ResourceQuota, and Kyverno. Four layers that decide whether your pod gets scheduled, throttled, or killed. Most of the confusion around _"exceeded quota"_ errors comes from not knowing which layer rejected you.

#### [In-Place Pod Resize](in-place-pod-resize.md)

Changing CPU and memory on a running container without a restart. A genuinely useful capability, and one that needs governance before it goes anywhere near production.
