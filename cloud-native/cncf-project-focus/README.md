---
description: >-
  Hands-on CNCF deep-dives organized by thematic arc — Infrastructure,
  Observability, AI-Native Platform. Working labs, Kyverno governance patterns,
  and lessons from a financial services practitioner.
---

# CNCF Project Focus

A bi-weekly series exploring CNCF graduated and incubating projects through hands-on labs, production deployments, and Kyverno governance policies.

Every episode follows the same structure: a working GitHub lab, a Medium deep-dive, and the governance policies I'd enforce if this ran in a regulated financial services platform. The series tries to show how these projects compose, episode by episode, into something that hangs together.

{% hint style="info" %}
📚 **Series hub on GitHub:** A central index maintained alongside this site, tracking every episode, every arc and every supporting artifact: [CNCF Project Focus Series](https://github.com/christian-dussol-cloud-native/cloud-native-knowledge-hub/blob/main/CNCF-Project-Focus-Series.md)
{% endhint %}

The series is organized into three arcs.

### Arc 1: Infrastructure Foundations

**Status: complete**

The plumbing layer. How do you compose serverless, infrastructure provisioning, and networking into a platform that scales beyond a single cloud and a single team?

* Episode 1, [Knative](arc-1-knative.md): Vendor-neutral serverless on Kubernetes
* Episode 2, [Crossplane](arc-1-crossplane.md): One Kubernetes API, any cloud provider
* Episode 3, [Cilium](arc-1-cillium.md): Kernel-native Kubernetes networking

### Arc 2: Observability

**Status: in progress**

You cannot optimize what you cannot see. From metrics collection to distributed tracing to service mesh, the observability layer is what turns a platform from operable to ownable.

* Episode 4, [Prometheus](arc-2-prometheus.md): Cloud-native metrics with FinOps-grade governance
* Episode 5, [OpenTelemetry](arc-2-opentelemetry.md): The unified observability pipeline
* Episode 6, Istio: Ambient mode and zero-trust networking — _in progress_

### Arc 3: AI-Native Platform

**Status: planned (2026)**

What changes when AI is the default workload on your platform? Model serving, AI gateways, agentic orchestration and the governance problems that come with all three.

* Episode 7: Kubeflow: ML pipelines on Kubernetes
* Episode 8: KServe: Model serving at scale
* Episode 9: KGateway: The AI gateway pattern
* Episode 10: KAgent: Agentic AI orchestration
