---
description: >-
  GPU tier fallback and model-aware inference routing, both runnable on a
  laptop. Simulated hardware, real scheduling and routing decisions.
---

# The AI substrate

Three floors of the AI substrate, made observable without hardware. The accelerators are simulated, the model server is a stand-in and the cluster is a discrete-event model, but the scheduling, routing and queueing decisions are real. That is the line these labs are careful to draw.

### Allocation: walking the Prioritized List cascade with DRA

**What it shows.** Three mock GPU tiers (H100, A100, L4) and a claim that says `firstAvailable`. Then a script that makes the top tier unavailable and lets you watch the scheduler descend: H100 gone, the pod lands on A100; A100 gone, it lands on L4. Declarative hardware heterogeneity, observed rather than described.

It runs on Kind with the SIG Node example driver, so the GPUs are simulated. The tutorial says so plainly: the scheduling and allocation are real, no CUDA workload runs. Swap in NVIDIA's driver in production and the manifests do not change, which is the whole point of a standard primitive.

**What it needs.** Kind, Docker, about 4 GB of RAM and thirty minutes. No GPU, no cloud, no cost.

→ [dra-prioritized-list-tutorial](https://github.com/christian-dussol-ai-native/dynamic-resource-allocation/tree/main/dra-prioritized-list-tutorial)

📄 The writing behind it: [Allocation: DRA](../ai-native/kubernetes-as-ai-substrate/allocation-dra.md)

#### What I learned

Prioritized lists give a workload something it never had: the ability to degrade instead of fail. Before, a claim for a specific accelerator either matched or the pod stayed Pending. Expressing an acceptable fallback in the manifest turns a scheduling failure into a scheduling decision, and that changes what you can promise a team about capacity.

The PersistentVolumeClaim analogy is not a teaching device, it is the actual design. Anyone who has requested storage in Kubernetes already knows how to request a GPU under DRA, which means the conceptual cost of adopting this is close to zero for a platform team.

And the barrier to learning accelerator scheduling has collapsed. A year ago this needed hardware. It now needs Kind and thirty minutes.

My first instinct for testing the cascade was wrong, and the correction is the lesson. Deleting a DeviceClass does not trigger the fallback: the scheduler expects the referenced class to exist and descends when no matching device is available within it. The wrong approach taught me more about the mechanism than the right one would have.

Simulated accelerators are enough to learn the allocation semantics, because the semantics are the standard. What changes in production is the driver underneath, not the manifests on top. That is the promise of a portable primitive, and it is testable on a laptop.

### Serving: what a simulator lets you learn without a GPU

**What it shows.** BLIS is a CPU-only, deterministic discrete-event simulator for LLM inference serving. This lab does not try to teach it exhaustively. It asks one question and answers it with commands you can run: **what can you actually learn about serving without touching a GPU, and where does silicon become unavoidable?**

Three labs. A survey of what the tool lets you declare, concluding nothing. One baseline run, to see it work and learn to read its output. Then roofline against trained-physics latency models, which is where calibration stops being an abstraction.

The grid underneath is what makes it more than a tutorial. Every mechanism gets three separate questions that are easy to collapse into one: can I **declare** it, is the mechanism **and its cost** modeled, and does that cost **match real hardware**? A flag that exists does not prove the simulator models what the dimension costs.

**What it needs.** Go 1.24, jq, about 2 GB of disk. Runs in seconds on a laptop. No GPU, and that is the point.

→ [blackbox-inference-simulator](https://github.com/christian-dussol-ai-native/blackbox-inference-simulator)

📄 The floor it belongs to: [Serving: llm-d](../ai-native/kubernetes-as-ai-substrate/serving-llm-d.md)

#### What I learned

The third level is mostly out of reach on a CPU, and saying so is the lab. BLIS publishes a calibration scope, 7 to 9% median error over 36 validation experiments on H100, A100 and L40S. Outside that scope fidelity is unknown, and no amount of CPU experimentation will establish it. That is a limit to state, not one to work around.

Writing the expectation down before running is the only part of the method I would call non-negotiable. The gap between what you predicted and what the simulator printed is the whole lesson, and it evaporates the moment you reconstruct it afterwards. Especially when the prediction was wrong.

Determinism changes what a lab can promise. Same seed, same version, same flags, identical output to the bit. A reader can reproduce a number rather than trust it, which is rare enough in this field to be worth the constraint.

And the honest caveat has to be first, not last. Simulated is not measured. Every number here is the output of a latency model, and the only defensible way to use one is to say so.

### Routing: model-aware inference routing with GAIE and agentgateway

**What it shows.** The three GAIE primitives wired together on Kind: an InferencePool grouping model servers, an Endpoint Picker the Gateway consults over ext-proc before every request, and an InferenceObjective declaring which workload wins when capacity is contended. A vLLM simulator stands in for a model server, so none of it needs a GPU.

The moment that lands is the response header. `x-inference-pod` names the exact pod the Endpoint Picker chose, so the routing decision stops being a claim you read and becomes something you can point at.

The InferenceObjective is the part worth dwelling on from a regulated seat. Priority between tenants expressed as a reviewable Kubernetes object rather than buried in code, which is the inference-layer echo of DRA's prioritized list.

**What it needs.** Kind, cloud-provider-kind, Helm and curl. No GPU, no cloud.

→ [gateway-api-inference-extension](https://github.com/christian-dussol-ai-native/gateway-api-inference-extension)

📄 The writing behind it: [Routing: Gateway API Inference Extension](../ai-native/kubernetes-as-ai-substrate/routing-gateway-api-inference-extension.md)

#### What I learned

How little of this is new, and that is the good news. It is the Gateway API a platform team already runs, with three inference-aware objects added. No new control plane, no new permission model, no separate operational story. The adoption cost for an organisation that already has Gateway API is measured in objects, not in migrations.

InferenceObjective is the piece I did not expect to care about most. Priority between tenants becomes a declarative object you can review in a pull request and show to an auditor, rather than a heuristic living inside a router. Under contention, the reason production was served before sandbox work is written down.

And the existence of a vLLM simulator is quietly a gift to the ecosystem. Learning a control plane without paying for the data plane is what makes this floor approachable at all.

The simulator cannot demonstrate the reason GAIE exists. Smarter routing that cuts latency and lifts GPU utilisation is precisely what a fake backend under no real load cannot show. This lab proves the plumbing works; whether the intelligence pays off is a question only a GPU cluster under load can answer. That is the honest line between what I tested and what I read.

The operational reality of beta software also stopped being abstract: a `gateway-channel` conflict in cloud-provider-kind cost real time, and no quickstart warns about it.
