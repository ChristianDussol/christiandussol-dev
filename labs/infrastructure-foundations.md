---
description: >-
  Serverless economics, a universal control plane and eBPF networking. Three
  labs where the governance layer decides whether the technology is safe to
  adopt.
---

# Infrastructure foundations

The first arc of CNCF Project Focus, made runnable. Serverless, control planes and networking, each with the policy layer that makes it safe to adopt rather than merely interesting.

### Serverless: scale-to-zero economics with Knative

**What it shows.** Scale-to-zero you can watch happen: send traffic, wait sixty seconds, see the pods disappear, send traffic again, see one come back in under a second. Then two Kyverno policies that make it non-optional in dev and staging, with a compliant and a non-compliant service side by side so you watch the admission webhook refuse one.

What sets this one apart is what it refuses to claim. A section on when **not** to use Knative, databases, queues, WebSockets, caches, anything needing instant availability, and a stated cold-start cost of roughly 300 ms to 1 s. The cost calculator ships with no numbers of its own: you feed it your service count, your usage hours, your rate. A tool that declines to tell you what you will save is more useful than one that promises a percentage.

**What it needs.** Minikube and kubectl. Nothing else.

→ [knative-cost-optimization](https://github.com/christian-dussol-cloud-native/knative/tree/main/knative-cost-optimization)

📄 The writing behind it: Episode 1: Knative

#### What I learned

Scale-to-zero is not a trade-off you tolerate, it is one you stop thinking about. Once the policy is in place, dev and staging cost nothing overnight and nobody had to change how they work.

The Knative Service object collapses Deployment, Service, HPA and Ingress into one resource. Less YAML to review, and fewer places for a policy to miss something. In a regulated environment that simplification is worth more than the cost saving, because every additional object is another thing an auditor has to trace.

Writing the list of cases where Knative is the wrong answer took longer than documenting where it fits, and it is the part I would keep if I had to cut the rest. A recommendation without a refusal is marketing.

A calculator that ships with no numbers forces the reader to confront their own usage data. Publishing a savings percentage would have been easier, more shareable, and less useful.

The cold start is a cost, not a footnote. Stating it as 300 ms to 1 s is what makes the rest of the argument credible.

### Control plane: one API across three clouds with Crossplane

**What it shows.** A database defined once, in business terms (size, engine, backup, cost centre), then provisioned on AWS RDS, Azure Database or Cloud SQL by changing a single label. No application code changes, no second tool.

The governance step is where it earns its place. The Kyverno policy sits on the abstraction, not on the provider: a DatabaseInstance without a cost-centre tag is refused whichever cloud it lands on. That is cost allocation enforced at the platform API rather than reconciled afterwards in three billing consoles.

**What it needs.** Minikube, plus a cloud account. The repo documents AWS Free Tier setup step by step.

→ [crossplane-first-sample](https://github.com/christian-dussol-cloud-native/crossplane/tree/main/crossplane-first-sample)

📄 The writing behind it: Episode 2: Crossplane

#### What I learned

The abstraction holds. A developer asks for a database in the vocabulary of the business, size and engine and backup and cost centre, and never learns what RDS calls a parameter group. That is the platform contract working as advertised, and it is rarer than the marketing suggests.

Because everything is a Kubernetes object, the whole estate inherits what Kubernetes already gives you: RBAC, audit logs, GitOps, drift correction. No second permission model, no second audit trail, no second tool to explain to a regulator.

Putting the policy on the abstraction rather than on each provider is what makes multi-cloud governance tractable. One rule covers three clouds, and the rule survives a provider change that would have invalidated three separate ones.

Switching cloud by changing a label looks like the demo trick. It is not: the composition behind it is where all the work lives, and the abstraction is only ever as good as that composition.

This is the one lab here that needs a cloud account. Vendor-neutral tooling does not mean vendor-free testing.

### Networking: eBPF, policy and observability with Cilium

**What it shows.** Cilium replacing iptables with eBPF, then three layers of policy on top: L3 deny-all, L4 port filtering, L7 HTTP method filtering. Hubble gives you the network view without an agent, so you watch a connection get dropped rather than inferring it from a timeout.

The part worth your time is the last third. A PCI-DSS payment architecture with treasury and trading namespaces, where Kyverno auto-generates the default-deny policy on namespace creation and refuses any pod missing its cost-centre labels. Zero Trust that nobody has to remember to apply.

**What it needs.** Minikube, 4 CPU and 8 GB. No cloud account.

→ [cilium-first-sample](https://github.com/christian-dussol-cloud-native/cilium/tree/main/cilium-first-sample)

📄 The writing behind it: Episode 3: Cilium

#### What I learned

Hubble changed what I could see rather than what I could configure. Watching a connection get dropped is a different kind of knowledge from reading that it should have been, and it turned network policy from something I reasoned about into something I observed.

L7 policy is the capability I underestimated. Allowing GET on a payment API while refusing POST, expressed in a Kubernetes object rather than in a service mesh sidecar, is a segmentation control an auditor can read directly. That is a shorter conversation than explaining an Envoy filter chain.

Generating the default-deny policy when a namespace is created, rather than asking a team to apply one, is the difference between a secure default and a security control that depends on memory. It is the version that survives turnover.

One correction I owe the reader. The performance comparison in the repository, iptables against eBPF, reports orders of magnitude that circulate widely in this ecosystem. They are not measurements I took, and I should have said so when I wrote them. They are directionally useful for framing the argument and they should not be cited as data.
