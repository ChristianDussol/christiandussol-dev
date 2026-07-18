---
description: >-
  Securing APIs and LLMs in financial services. The OWASP Top 10s, read from
  production rather than from a checklist, with Kyverno as the enforcement
  layer.
---

# Security

## Security

Two OWASP Top 10s, ten years apart. One for APIs, one for LLMs. Both describe the same thing: the predictable ways systems fail when nobody is enforcing the boundary.

I write about security from the position I actually occupy, which is a platform one. I am not a penetration tester. I am the person who has to make sure that the mistake, once identified, cannot reach production again. That distinction shapes everything here: less about finding the vulnerability, more about the policy that prevents its class.

### In this section

#### [API Security Reality Check](api-security-reality-check.md)

What years of securing financial APIs actually taught me. The OWASP API Security Top 10 read through the 4C model, why a single code oversight becomes a cloud-level breach, and how Kyverno turns reactive testing into proactive prevention.

#### [OWASP LLM Top 10](owasp-llm-top-10.md)

The ten critical risks of running LLMs in production, with the financial services impact spelled out. Prompt injection, sensitive data disclosure, excessive agency, and what each one actually costs when the model sits in front of customer data.
