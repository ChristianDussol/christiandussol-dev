---
description: >-
  Hands-on CNCF deep-dives organized by thematic arc: infrastructure,
  observability, AI native infrastructure and platform. Working labs and
  governance patterns.
---

# CNCF Project Focus

A bi-weekly series exploring CNCF graduated and incubating projects through hands-on labs, production deployments, and Kyverno governance policies.

Every episode follows the same structure: a working GitHub lab, a Medium deep-dive, and the governance policies I'd enforce if this ran in a regulated financial services platform. The series tries to show how these projects compose, episode by episode, into something that hangs together.

{% hint style="info" %}
📚 **Series hub on GitHub:** A central index maintained alongside this site, tracking every episode, every arc and every supporting artifact: [CNCF Project Focus Series](https://github.com/christian-dussol-cloud-native/cloud-native-knowledge-hub/blob/main/CNCF-Project-Focus-Series.md)
{% endhint %}

The series is organized into four arcs.

## Arc 1: Infrastructure Foundations

**Status: complete**

The plumbing layer. How do you compose serverless, infrastructure provisioning, and networking into a platform that scales beyond a single cloud and a single team?

* Episode 1, [Knative](arc-1-knative.md): Vendor-neutral serverless on Kubernetes
* Episode 2, [Crossplane](arc-1-crossplane.md): One Kubernetes API, any cloud provider
* Episode 3, [Cilium](arc-1-cilium.md): Kernel-native Kubernetes networking

## Arc 2: Observability

**Status: complete**

You cannot optimize what you cannot see. From metrics collection to distributed tracing to service mesh, the observability layer is what turns a platform from operable to ownable. Measure, trace, control.

* Episode 4, [Prometheus](arc-2-prometheus.md): Cloud-native metrics with FinOps-grade governance
* Episode 5, [OpenTelemetry](arc-2-opentelemetry.md): The unified observability pipeline
* Episode 6, [Istio](arc-2-istio.md): Service mesh, ambient mode and zero-trust networking

## Arc 3: AI Native Infrastructure

**Status: next**

One question runs through the whole arc: how do you make an AI workload fit on hardware that was never sized for it? Sharing the accelerator, feeding it fast enough to keep it busy, and deciding which job gets in and when. Every episode has to show a primitive that Kubernetes absorbs, otherwise it does not belong here.

* Episode 7, HAMi: Accelerator sharing, for when a whole GPU is more than the workload needs
* Episode 8, Fluid: Feeding the compute, because load time belongs to elasticity rather than to storage tuning
* Episode 9, Kueue and Volcano: Batch admission and gang scheduling, the right to enter

The three compose into one chain: what the workload runs on, how it is fed, and who is allowed in. It is also where the CNCF draws its own line, with the AI Inference and Agentic track at KubeCon separating scheduling and accelerator utilization from model serving and routing.

## Arc 4: AI Native Platform

**Status: planned**

Once the workload fits on the hardware, a different question starts, and it belongs on its own floor: how is a model's lifecycle orchestrated, how is it served, how is an agent executed?

* Episode 10, Kubeflow: Model lifecycle on Kubernetes
* Episode 11, KServe: Model serving at scale
* Episode 12, KAgent: Agentic orchestration
