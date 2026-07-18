---
description: >-
  Why your pods keep getting rejected. Pod resources, LimitRange, ResourceQuota
  and Kyverno, and which of the four layers is actually blocking you.
---

# Resource management

## Why your pods keep getting rejected.

Thirty minutes before a demo to stakeholders, the environment goes down. The deployment is rejected with `exceeded quota: requests.cpu` and nobody knows why.

That error is not one problem, it is four possible problems wearing the same message. Pod resources, LimitRange, ResourceQuota, and Kyverno each reject deployments for different reasons, and knowing which layer said no is most of the work.

📎 **Visual companion**: [Kubernetes Resource Management carousel (PDF)](https://github.com/christian-dussol-cloud-native/kubernetes/blob/main/carousel/Kubernetes%20Resource%20Management.pdf)

### What the article covers

* **The four-layer governance stack.** Pod resources are the contract. LimitRange sets the size rails. ResourceQuota holds the budget. Kyverno enforces the policy and auto-remediates. They only work together
* **Requests versus limits, and the asymmetry that bites.** CPU is compressible: exceed the limit and you get throttled. Memory is not: exceed it and the container is killed. That single difference explains most production surprises
* **LimitRange as a guardrail.** How it blocks the resize that would have taken a container from 2 CPUs to 32, and why `maxLimitRequestRatio` is the field nobody sets and everybody needs
* **ResourceQuota and the sprawl problem.** Teams do not blow their budget in one go. They creep, one reasonable-looking increase at a time
* **Kyverno beyond native constraints.** Native LimitRange is static and rejects. Kyverno is contextual and can mutate: auto-adding default resources instead of blocking the developer, enforcing limit/request ratios, applying different rules in production than in dev
* **Resizing as an attack vector.** Gradual resource increases are how cryptomining hides. Governance is a security control, not just a cost control
* **The troubleshooting section.** Five common error messages, what each one actually means, and the command that tells you which layer rejected you

### Read

* **Medium article**: [Why Your Kubernetes Pods Keep Getting Rejected](https://medium.com/@christian.dussol/why-your-kubernetes-pods-keep-getting-rejected-the-resource-management-guide-you-actually-need-48ea965eb038)
* **GitHub**: [k8s-resources-management.md](https://github.com/christian-dussol-cloud-native/kubernetes/blob/main/guides/k8s-resources-management.md)
