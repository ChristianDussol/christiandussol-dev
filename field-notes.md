---
description: >-
  Reflections on the cloud-native landscape and the shifts reshaping the
  industry. Signals tracked, tools evaluated, field reports from production.
---

# Field Notes

Reflections on the cloud-native landscape and the shifts reshaping the industry. Not tutorials, and not verdicts either. These are field reports: observations from someone deploying these technologies in production, watching how the field evolves, and trying to make sense of where it's heading.

***

## Signals

_A recurring format. Not articles, just what I am tracking, with a line or two on why each matters for engineering strategy. Published when the picture moves meaningfully._

#### What I'm Reading in the CNCF AI Ecosystem

**June 2026.** Four signals from KubeCon EU and the broader ecosystem, moving faster than the release notes reveal. NVIDIA donating its GPU DRA driver to the CNCF, which turns accelerator scheduling from a vendor negotiation into a portable capability. AI Conformance growing from 18 to 31 certified platforms in five months, and the coming pivot from self-assessment to automated validation, which is where the program's credibility gets tested. llm-d entering the Sandbox alongside Kueue and the Gateway API Inference Extension, which is the moment the CNCF AI stack stops being a loose collection and starts being a layer. And OpenTelemetry graduating, with observability now a conformance pillar.

The pattern underneath: conformance is becoming a procurement filter. When an enterprise asks whether your platform is AI-ready, they will increasingly mean whether it is on the CNCF list.

→ [LinkedIn Pulse](https://www.linkedin.com/pulse/what-im-reading-cncf-ai-ecosystem-field-note-june-2026-dussol-kaece) · [Medium](https://medium.com/@christian.dussol/what-im-reading-in-the-cncf-ai-ecosystem-field-note-june-2026-be2c0d37f3c5)

***

## Where the industry is heading

_Two pieces written after KubeCon Amsterdam 2026, when several things I believed turned out to be wrong._

#### Digital Sovereignty: What I Got Wrong

I arrived in Amsterdam believing sovereignty meant building walls. Five keynotes later, I understood it differently: sovereignty is not about where your workloads run, it is about the freedom to move them. Two of the keynote speakers commented on the article to confirm that none of the sovereignty keynotes had been coordinated beforehand.

→ [LinkedIn Pulse](https://www.linkedin.com/pulse/digital-sovereignty-what-i-got-wrong-christian-dussol-1elxe) · [Medium](https://medium.com/@christian.dussol/digital-sovereignty-what-i-got-wrong-56cba6cb633a?sharedUserId=christian.dussol)

#### The AI-Native Shift: What KubeCon Amsterdam Made Me Realize About a Decade of Cloud Native

The shift from cloud-native to AI-native is happening. The platform engineering playbook has to adapt rather than repeat itself. What a decade of cloud-native taught us, and what it did not prepare us for.

→ [LinkedIn Pulse](https://www.linkedin.com/pulse/ai-native-shift-what-kubecon-amsterdam-made-me-realize-dussol-gauhe) · [Medium](https://medium.com/@christian.dussol/the-ai-native-shift-what-kubecon-amsterdam-made-me-realize-about-a-decade-of-cloud-native-39e7ac996935?sharedUserId=christian.dussol)

***

## Choosing what to adopt, and what to refuse

_Honest evaluations. What the tool actually does when you deploy it, rather than what the conference talk promised._

#### Why Does Backstage Work, and Under What Conditions? Notes from an Investigation

Not a verdict. A field report from an ongoing investigation: three materials, three hypotheses I am starting to trust, two honest uncertainties, and one coda about why the window to get this right is smaller than we think. Seasoned in the problem, beginner on this particular answer.

→ [LinkedIn Pulse](https://www.linkedin.com/pulse/why-does-backstage-work-under-what-conditions-notes-from-dussol-p33re) · [Medium](https://medium.com/@christian.dussol/why-does-backstage-work-and-under-what-conditions-notes-from-an-investigation-dc3d1c224663)

#### Why Kyverno Became My Go-To Solution for Kubernetes Security and Compliance

Kyverno's Kubernetes-native YAML approach makes policy-as-code accessible where OPA and Rego raise the bar too high for most platform teams. Why I chose it, what it cost me to learn, and where it still falls short.

→ [Medium](https://medium.com/@christian.dussol/why-kyverno-became-my-go-to-solution-for-kubernetes-security-and-compliance-5136450786cf?sharedUserId=christian.dussol)

***

## How teams work, how engineers learn

_The human side of platform engineering. Structure and skill, which turn out to be the same problem._

#### Team Topologies: The Blueprint for Cloud & AI Transformations

Why the four team types and three interaction modes still hold up as the blueprint, now for AI transformations as much as cloud ones. Conway's Law does not care about your org chart.

→ [Medium](https://medium.com/@christian.dussol/team-topologies-the-blueprint-for-cloud-ai-transformations-e255475d50a0?sharedUserId=christian.dussol)

#### How Scott Young's Ultra-Learning Method Changed How I Learned Kubernetes

Deliberate practice applied to a moving target. Why certifications are forcing functions rather than credentials, and how the method compresses years into months when applied rigorously.

→ [Medium](https://medium.com/@christian.dussol/how-scott-youngs-ultra-learning-method-has-changed-how-i-learned-kubernetes-d66e7d4ac075?sharedUserId=christian.dussol)

***
