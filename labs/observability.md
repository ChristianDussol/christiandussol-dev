---
description: >-
  Metrics and traces are only worth collecting if something guarantees their
  inputs. Two labs where governance at admission is what makes the data usable.
---

# Observability

The second arc, and the place where the argument of this whole section is clearest. Both labs make the same point from different ends: the quality of what you observe is decided at admission, before any collector runs.

## Metrics: cost attribution with Prometheus and Kyverno

**What it shows.** The kube-prometheus-stack with PromQL query sets for cost attribution, waste detection, capacity forecasting and SLO tracking, plus two Grafana dashboards. A deliberately over-provisioned workload ships with it, so the waste queries have something real to find.

The argument sits in the loop. Kyverno enforces resource limits and cost labels at admission, which is what makes the metrics mean anything: a pod without limits produces utilisation data you cannot act on. Governance first, then measurement, then dashboards that feed the next policy review.

**What it needs.** A local cluster (Minikube, kind or k3d), 4 CPU and 8 GB. Nothing else.

→ [prometheus-first-sample](https://github.com/christian-dussol-cloud-native/prometheus/tree/main/prometheus-first-sample)

📄 The writing behind it: [Episode 4: Prometheus](../cloud-native/cncf-project-focus/arc-2-prometheus.md)

## Traces: a unified telemetry pipeline with OpenTelemetry

**What it shows.** An OTel Collector gateway, zero-code auto-instrumentation, and a three-service demo (Order, Payment, Inventory) whose calls you follow end to end in Jaeger. Traces, metrics and logs leave through one pipeline instead of three agents.

Two parts earn their keep. Head and tail sampling, presented as a cost decision rather than a config option: you choose how much telemetry is worth keeping. And the same governance loop as the metrics lab, applied to instrumentation. Without enforcement, a service ships without OTel annotations and its failures are simply invisible.

**What it needs.** Minikube, 4 CPU and 8 GB. Nothing else.

→ [opentelemetry-first-sample](https://github.com/christian-dussol-cloud-native/opentelemetry/tree/main/opentelemetry-first-sample)

📄 The writing behind it: [Episode 5: OpenTelemetry](../cloud-native/cncf-project-focus/arc-2-opentelemetry.md)
