---
description: >-
  Metrics and traces are only worth collecting if something guarantees their
  inputs. Two labs where governance at admission is what makes the data usable.
---

# Observability

The second arc, and the place where the argument of this whole section is clearest. Both labs make the same point from different ends: the quality of what you observe is decided at admission, before any collector runs.

### Metrics: cost attribution with Prometheus and Kyverno

**What it shows.** The kube-prometheus-stack with PromQL query sets for cost attribution, waste detection, capacity forecasting and SLO tracking, plus two Grafana dashboards. A deliberately over-provisioned workload ships with it, so the waste queries have something real to find.

The argument sits in the loop. Kyverno enforces resource limits and cost labels at admission, which is what makes the metrics mean anything: a pod without limits produces utilisation data you cannot act on. Governance first, then measurement, then dashboards that feed the next policy review.

**What it needs.** A local cluster (Minikube, kind or k3d), 4 CPU and 8 GB. Nothing else.

→ [prometheus-first-sample](https://github.com/christian-dussol-cloud-native/prometheus/tree/main/prometheus-first-sample)

📄 The writing behind it: Episode 4: Prometheus

#### What I learned

The PromQL queries turned out to be the durable artefact. Once a query expresses cost per team or waste per namespace correctly, it keeps working across clusters and across years, because the metric names are a stable contract. That is a rare property in this ecosystem, and it is why the query files outlived the dashboards I built on top of them.

Once the labels are enforced, PromQL stops being a monitoring language and becomes a finance one. The same expression that shows CPU utilisation shows spend per cost centre, with no additional tooling. The FinOps capability was already in the cluster, waiting for the label hygiene to make it usable.

Metrics from pods without limits are not merely incomplete, they are misleading. Utilisation measured against no ceiling is a number with no denominator, and a dashboard full of them looks informative while telling you nothing.

Shipping a deliberately over-provisioned workload was the right call. A waste-detection query with nothing to detect teaches nobody anything.

### Traces: a unified telemetry pipeline with OpenTelemetry

**What it shows.** An OTel Collector gateway, zero-code auto-instrumentation, and a three-service demo (Order, Payment, Inventory) whose calls you follow end to end in Jaeger. Traces, metrics and logs leave through one pipeline instead of three agents.

Two parts earn their keep. Head and tail sampling, presented as a cost decision rather than a config option: you choose how much telemetry is worth keeping. And the same governance loop as the metrics lab, applied to instrumentation. Without enforcement, a service ships without OTel annotations and its failures are simply invisible.

**What it needs.** Minikube, 4 CPU and 8 GB. Nothing else.

→ [opentelemetry-first-sample](https://github.com/christian-dussol-cloud-native/opentelemetry/tree/main/opentelemetry-first-sample)

📄 The writing behind it: Episode 5: OpenTelemetry

#### What I learned

Zero-code instrumentation genuinely works, and that still surprises me. An annotation on a pod, no import, no library, no redeployment of a code change, and the traces appear. For an estate where touching legacy services is a change-request conversation, that is the difference between observability you plan for and observability you can actually get.

The Collector as a single egress point is worth more than the vendor neutrality it is usually sold on. One place where telemetry leaves the cluster is one place to filter PII, one place to enforce retention, one place an auditor asks about. Three agents would have meant three of each.

Sampling is a cost decision before it is a configuration option. Head versus tail is really a question about how much telemetry is worth paying to keep, and framing it as a config choice hides the decision from the people who should be making it.

An uninstrumented service does not fail loudly, it fails invisibly. That asymmetry is why the annotation belongs at admission rather than in a team's checklist: nobody notices the traces that were never emitted.
