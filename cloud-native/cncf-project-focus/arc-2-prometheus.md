---
description: >-
  Prometheus as the metrics substrate rather than a monitoring tool. PromQL
  patterns for cost attribution, kube-prometheus-stack, and Kyverno label
  hygiene.
---

# Cloud-Native Metrics with FinOps-Grade Governance

The first episode of Arc 2 treats Prometheus not as a monitoring tool but as the metrics substrate of the entire observability stack. PromQL for FinOps, kube-prometheus-stack as a reference deployment and the governance layer that turns raw metrics into actionable cost data.

<figure><img src="https://3864580007-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F782Y46kG3IDKMjaaCmCh%2Fuploads%2F7Q0jOK9WcsCAtfsN7kkc%2F1.png?alt=media&#x26;token=ea67d885-0fcd-4287-85cf-749fd0e1f52f" alt="" width="563"><figcaption></figcaption></figure>

## 📎Visual companion

[CNCF Project Focus #4: Prometheus carousel (PDF)](https://github.com/christian-dussol-cloud-native/prometheus/blob/main/carousel/CNCF%20Project%20Focus%20%234%20-%20Prometheus.pdf)

## **What the episode covers**

* kube-prometheus-stack deployment patterns
* PromQL patterns for cost attribution and right-sizing
* Kyverno policies for metric hygiene and label enforcement
* The Grafana dashboards I actually use in production

## **Read the deep-dive**

* **Medium article**: [Prometheus: Not just Monitoring, the Foundation of every cost decision you’ll make](https://medium.com/@christian.dussol/prometheus-not-just-monitoring-the-foundation-of-every-cost-decision-youll-make-50ae3c2c0beb)
* **GitHub lab**: [github.com/christian-dussol-cloud-native/prometheus](https://github.com/christian-dussol-cloud-native/prometheus)
* **Runnable lab**: [Metrics: cost attribution with Prometheus and Kyverno](../../labs/observability.md)
