---
description: >-
  The ten critical risks of running LLMs in production, with the financial
  services impact spelled out. Prompt injection, data disclosure, excessive
  agency.
---

# OWASP LLM Top 10

## OWASP LLM Top 10 (2025)

Ten critical risks you have to know before the model touches customer data.

Ninety percent of organizations deploy LLMs. Five percent feel security-ready. Thirty-five percent of incidents come from simple prompts.

That gap is the whole problem. The OWASP LLM Top 10 exists because the failure modes are already predictable, already documented, and already being exploited. This carousel walks through them with the financial services impact spelled out, because "the model leaked something" reads differently when the something is a credit scoring formula.

📎 **Visual companion**: [OWASP LLM Top 10 2025 carousel (PDF)](https://github.com/christian-dussol-cloud-native/cloud-security/blob/main/carousel/OWASP%20LLM%20Top%2010%202025.pdf)

### What the carousel covers

**Critical**

* **LLM01: Prompt Injection.** The attack that needs no exploit, only a sentence
* **LLM02: Sensitive Data Disclosure.** Training data extraction, cross-conversation leakage, PII surfacing in responses
* **LLM06: Excessive Agency.** What happens when the model can do more than it should

**High risk**

* **LLM07: System Prompt Leakage.** Your business logic exposed in minutes. Credit scoring formulas revealed, fraud detection rules exposed
* **LLM08: Vector and Embedding Weaknesses.** The attack surface nobody audits

**Also in the Top 10**

* LLM03: Supply Chain Vulnerabilities
* LLM04: Data and Model Poisoning
* LLM05: Insecure Output Handling
* LLM09: Misinformation
* LLM10: Unbounded Consumption

Each risk comes with the defense layers that actually hold: prompt isolation, output filtering, PII detection, differential privacy, user context isolation.

### Source

* **Official reference**: [OWASP LLM Top 10 (2025)](https://genai.owasp.org/llm-top-10/)
