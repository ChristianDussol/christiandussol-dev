# Episode 6: Istio

**Service mesh for Kubernetes.**

Arc 2 asked three questions in order. Prometheus measures. OpenTelemetry traces. **Istio controls.**

Look at a single service-to-service call and five questions appear at once. Is it encrypted. Is the caller authorized. What is the latency, what are the errors, where is the telemetry. At fifty services the arithmetic turns hostile: up to 2,450 possible call paths, and every team rebuilding retries, timeouts and TLS its own way.

A service mesh moves that layer out of the application. **The app keeps business logic. The mesh handles security, traffic and telemetry.**

### 📎Visual companion

[CNCF Project Focus #6: Istio carousel (PDF)](https://github.com/christian-dussol-cloud-native/istio/blob/main/carousel/CNCF%20Project%20Focus%20%236%20-%20Istio.pdf)

### What the episode covers

* **What Istio is, and the eight years behind it.** Born in 2017 at Google and IBM on top of Envoy, ambient mesh introduced in 2022, CNCF Graduated in July 2023, ambient mode GA in 1.24
* **The architecture in one sentence.** You declare, istiod distributes, the proxies enforce. Config through xDS, identity through a built-in CA
* **Zero trust in eight lines.** A mesh-wide `PeerAuthentication` in STRICT mode, and plaintext stops being accepted anywhere. Then an `AuthorizationPolicy` so that only service A may call service B, by workload identity rather than by IP
* **Traffic through the Gateway API.** A 90/10 split to a v2 and a two-second request timeout, expressed in an `HTTPRoute` rather than in a vendor CRD
* **Observability for free.** `istio_requests_total` gives you 5xx by caller on a service you never instrumented. Latency, traffic and errors, which is the base you need before writing an SLO
* **Ambient mode, and why it changes the trade-off.** No sidecars: one ztunnel per node handling L4 and mTLS over HBONE, with an optional waypoint for L7. **L4 everywhere, L7 only where you need it**

### Read the deep-dive

* **Medium article**: _publishing shortly_
* **GitHub lab**: [github.com/christian-dussol-cloud-native/istio](https://github.com/christian-dussol-cloud-native/istio)
* **Runnable lab**: [Service mesh telemetry with Istio](../../labs/observability.md)

The lab runs on kind with Istio 1.31 in ambient mode and Gateway API v1.6, five steps mapped one to one onto the carousel slides. The most instructive of them is the one where a correct policy breaks the moment a waypoint enters the path.
