---
description: >-
  The code behind the writing. Three GitHub organizations covering cloud-native,
  cloud computing, and AI-native infrastructure. Labs, policies, guides, and
  builds.
---

# GitHub Knowledge

## Knowledge Hub

The code behind the writing.

Every series here starts with something that runs: an applied policy, a working lab, a build that broke and then did not. The article is the explanation. The repository is the proof. This page is the index to all of it.

The work is split across three organizations, mirroring the three domains this site covers.

***

### Cloud Native

CNCF projects, Kubernetes internals, policy-as-code, and security. The infrastructure foundation.

[**Cloud Native Knowledge Hub**](https://github.com/christian-dussol-cloud-native/cloud-native-knowledge-hub) Educational resources on cloud-native technologies. The entry point to this organization.

Also here:

* [**kubernetes**](https://github.com/christian-dussol-cloud-native/kubernetes), the guides, carousels, and feature demos (in-place pod resize, resource management, command reference)
* [**cloud-security**](https://github.com/christian-dussol-cloud-native/cloud-security), the OWASP API Security and LLM Top 10 material
* CNCF Project Focus labs, one per episode

→ [Browse the organization](https://github.com/christian-dussol-cloud-native)

***

### Cloud Computing

Hyperscaler architecture and cloud financial management. The layer underneath.

[**Cloud Computing Knowledge Hub**](https://github.com/christian-dussol-cloud-computing/cloud-computing-knowledge-hub) Educational resources on cloud computing technologies. The entry point to this organization.

Also here:

* [**microsoft-azure**](https://github.com/christian-dussol-cloud-computing/microsoft-azure), including the [AZ-305 Architecture Decision Guides](https://github.com/christian-dussol-cloud-computing/microsoft-azure/blob/main/certifications/AZ-305/architecture-decision-guides/README.md)
* [**FinOps**](https://github.com/christian-dussol-cloud-computing/FinOps), the carousel and supporting material

→ [Browse the organization](https://github.com/christian-dussol-cloud-computing)

***

### AI Native

The AI substrate: accelerator allocation, distributed inference, routing and the agentic layer.

[**AI Native Hub**](https://github.com/christian-dussol-ai-native/ai-native-hub) Practical resources for running AI and ML workloads on Kubernetes, indexed by domain. The entry point to this organization.

Also here:

* [**dynamic-resource-allocation**](https://github.com/christian-dussol-ai-native/dynamic-resource-allocation), GPU scheduling with DRA, including the [Prioritized List tutorial](https://github.com/christian-dussol-ai-native/dynamic-resource-allocation/tree/main/dra-prioritized-list-tutorial): a hands-on lab for GPU tier fallback, runnable on Kind
* [**gateway-api-inference-extension**](https://github.com/christian-dussol-ai-native/gateway-api-inference-extension), model-aware request routing for LLM inference (GAIE and agentgateway). Reproducible on Kind, no GPU required

→ [Browse the organization](https://github.com/christian-dussol-ai-native)

***

### Why three organizations

Not an accident, and not tidiness for its own sake. The three domains have different audiences, different lifecycles, and different reasons to exist.

Cloud Native is where the CNCF work lives, and it is the org most likely to be read by people who will never read the articles. Cloud Computing is more instructional: study material, decision guides, things I wrote to learn and left public. AI Native is the newest and the least settled, because the ground under it is still moving.

Splitting them keeps each one legible. Merging them would produce a single repository list nobody can navigate.
