---
description: >-
  Serverless economics, a universal control plane and eBPF networking. Three
  labs where the governance layer decides whether the technology is safe to
  adopt.
---

# Infrastructure foundations

The first arc of CNCF Project Focus, made runnable. Serverless, control planes and networking, each with the policy layer that makes it safe to adopt rather than merely interesting.

## Serverless: scale-to-zero economics with Knative

**What it shows.** Scale-to-zero you can watch happen: send traffic, wait sixty seconds, see the pods disappear, send traffic again, see one come back in under a second. Then two Kyverno policies that make it non-optional in dev and staging, with a compliant and a non-compliant service side by side so you watch the admission webhook refuse one.

What sets this one apart is what it refuses to claim. A section on when **not** to use Knative, databases, queues, WebSockets, caches, anything needing instant availability, and a stated cold-start cost of roughly 300 ms to 1 s. The cost calculator ships with no numbers of its own: you feed it your service count, your usage hours, your rate. A tool that declines to tell you what you will save is more useful than one that promises a percentage.

**What it needs.** Minikube and kubectl. Nothing else.

→ [knative-cost-optimization](https://github.com/christian-dussol-cloud-native/knative/tree/main/knative-cost-optimization)

📄 The writing behind it: [Episode 1: Knative](../cloud-native/cncf-project-focus/arc-1-knative.md)

## Control plane: one API across three clouds with Crossplane

**What it shows.** A database defined once, in business terms (size, engine, backup, cost centre), then provisioned on AWS RDS, Azure Database or Cloud SQL by changing a single label. No application code changes, no second tool.

The governance step is where it earns its place. The Kyverno policy sits on the abstraction, not on the provider: a DatabaseInstance without a cost-centre tag is refused whichever cloud it lands on. That is cost allocation enforced at the platform API rather than reconciled afterwards in three billing consoles.

**What it needs.** Minikube, plus a cloud account. The repo documents AWS Free Tier setup step by step.

→ [crossplane-first-sample](https://github.com/christian-dussol-cloud-native/crossplane/tree/main/crossplane-first-sample)

📄 The writing behind it: [Episode 2: Crossplane](../cloud-native/cncf-project-focus/arc-1-crossplane.md)

## Networking: eBPF, policy and observability with Cilium

**What it shows.** Cilium replacing iptables with eBPF, then three layers of policy on top: L3 deny-all, L4 port filtering, L7 HTTP method filtering. Hubble gives you the network view without an agent, so you watch a connection get dropped rather than inferring it from a timeout.

The part worth your time is the last third. A PCI-DSS payment architecture with treasury and trading namespaces, where Kyverno auto-generates the default-deny policy on namespace creation and refuses any pod missing its cost-centre labels. Zero Trust that nobody has to remember to apply.

**What it needs.** Minikube, 4 CPU and 8 GB. No cloud account.

→ [cilium-first-sample](https://github.com/christian-dussol-cloud-native/cilium/tree/main/cilium-first-sample)

📄 The writing behind it: [Episode 3: Cilium](../cloud-native/cncf-project-focus/arc-1-cilium.md)
