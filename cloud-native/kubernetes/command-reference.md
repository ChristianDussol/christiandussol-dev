---
description: >-
  A kubectl toolkit organized by role rather than alphabetically. Developer,
  admin, security, troubleshooting, monitoring, and Kyverno workflows.
---

# Command reference

### From kubectl chaos to command mastery.

My first Kubernetes troubleshooting session was humbling. Pods crashing, `CrashLoopBackOff` on screen, and a two-hour debugging session that consisted mostly of pasting commands from Stack Overflow and hoping one of them would say something useful.

The problem was not Kubernetes. It was my approach. I was treating kubectl as a black box and trying commands at random until something stuck.

Every cheat sheet I could find was organized alphabetically or by resource type. Nobody had organized commands by how teams actually work. So I built one.

📎 **Visual companion**: [Kubernetes Command Reference Guide carousel (PDF)](https://github.com/christian-dussol-cloud-native/kubernetes/blob/main/carousel/Kubernetes%20-%20Command%20reference%20guide.pdf)

### What the article covers

* **Why role beats alphabet.** Developers need speed. Administrators need control. Security engineers need enforcement. SREs need diagnostic velocity. The same command list serves none of them well
* **Developer toolkit.** Imperative commands, the `$do` dry-run variable that generates working YAML instead of writing it from scratch, ConfigMap patterns, and service exposure mapped to actual use cases
* **Administrator toolkit.** The cordon/drain/uncordon pattern for node maintenance, RBAC broken into a four-step workflow, resource quotas, and a namespace strategy that is not just `default`
* **Security toolkit.** Zero-trust network policies, Pod Security Standards, and secret management, prompted by a `privileged: true` pod that reached QA and was caught in an audit
* **Troubleshooting toolkit.** The `--previous` logs flag, the event stream, and the netshoot pattern for network debugging. A CrashLoopBackOff at 3:42 AM has a workflow, and it is worth having it memorized
* **Monitoring and Kyverno.** Metrics server, log aggregation, health probes, and the policies that automate governance so it does not depend on anyone remembering

### The principle underneath

Organization beats memorization. Do not memorize commands, organize them by workflow. When you need to deploy, you look at the deployment section. When you are debugging at 2 AM, you look at the debug section.

Speed in Kubernetes is not about knowing every command. It is about having the right ones organized for the moment you are in.

### Read

* **Medium article**: [How I Built My Kubernetes Command Toolkit](https://medium.com/@christian.dussol/how-i-built-my-kubernetes-command-toolkit-a-journey-from-kubectl-chaos-to-command-mastery-dad81c91327a)
* **GitHub**: [k8s-cheatsheet.md](https://github.com/christian-dussol-cloud-native/kubernetes/blob/main/guides/k8s-cheatsheet.md)
