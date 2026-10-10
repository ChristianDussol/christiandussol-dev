# Episode 6: Istio

**Service mesh for Kubernetes.**

Arc 2 asked three questions in order. Prometheus measures. OpenTelemetry traces. **Istio controls.**

Look at a single service-to-service call and five questions appear at once. Is it encrypted. Is the caller authorized. What is the latency, what are the errors, where is the telemetry. At fifty services the arithmetic turns hostile: up to 2,450 possible call paths, and every team rebuilding retries, timeouts and TLS its own way.

A service mesh moves that layer out of the application. **The app keeps business logic. The mesh handles security, traffic and telemetry.**

<figure><img src="../../.gitbook/assets/1 (12).png" alt=""><figcaption></figcaption></figure>

### 📎Visual companion

[CNCF Project Focus #6: Istio carousel (PDF)](https://github.com/christian-dussol-cloud-native/istio/blob/main/carousel/CNCF%20Project%20Focus%20%236%20-%20Istio.pdf)

### What the episode covers

* **What Istio is, and the eight years behind it.** Born in 2017 at Google and IBM on top of Envoy, ambient mesh introduced in 2022, CNCF Graduated in July 2023, ambient mode GA in 1.24
* **The architecture in one sentence.** You declare, istiod distributes, the proxies enforce. Config through xDS, identity through a built-in CA
* **Zero trust in eight lines.** A mesh-wide `PeerAuthentication` in STRICT mode, and plaintext stops being accepted anywhere. Then an `AuthorizationPolicy` so that only service A may call service B, by workload identity rather than by IP
* **Traffic through the Gateway API.** A 90/10 split to a v2 and a two-second request timeout, expressed in an `HTTPRoute` rather than in a vendor CRD
* **Observability for free.** `istio_requests_total` gives you 5xx by caller on a service you never instrumented. Latency, traffic and errors, three of the four golden signals, the same way for every service whoever wrote it
* **Ambient mode, and why it changes the trade-off.** No sidecars: one ztunnel per node handling L4 and mTLS, with an optional waypoint for L7. **L4 everywhere, L7 only where you need it**
* **And whether you need one at all.** A mesh is infrastructure you operate. The article says plainly when it is not worth it: a few services in one repository, no platform team to run it, or nothing to take out of the services in the first place

### Read the deep-dive

* **Medium article**: [Understanding Istio: a hands-on introduction to the service mesh](https://medium.com/@christian.dussol/understanding-istio-a-hands-on-introduction-to-the-service-mesh-04b162b83480)
* **GitHub lab**: [github.com/christian-dussol-cloud-native/istio](https://github.com/christian-dussol-cloud-native/istio)
* **Runnable lab**: [Service mesh telemetry with Istio](../../labs/observability.md)

The lab runs on a laptop in about 45 minutes, on kind with Istio in ambient mode, every step mapped onto a carousel slide. The most instructive of them is the one where a correct policy breaks the moment a waypoint enters the path.
