---
description: >-
  The auditor Skill finds the gap. The generator Skill fills it. Cross-skill
  composition, an 8-dimension audit engine, and why Skills are an ecosystem.
---

# Part 3: When Skills talk to each other

## Compose: a Skill can call another Skill

The third part is the climax of the first half of the series. It introduces a second Skill, `kyverno-policy-auditor` , that runs an 8-dimension audit on existing policies. When the auditor detects a gap, it triggers the generator from Part 2 to produce the missing artifact.

This is the moment Skills stop being tools and become an ecosystem.

<figure><img src="../../.gitbook/assets/1 (5).png" alt="" width="563"><figcaption></figcaption></figure>

### What the article covers

* The 4-step audit workflow built into `kyverno-policy-auditor`
* The 8 audit dimensions: security posture, compliance mapping, performance, governance, maintainability, testability, scope accuracy, exception handling
* The `audit_policy.py` architecture that makes scoring deterministic
* Cross-skill composition: how the auditor identifies a problem and another Skill solves it
* Why scripts can be the product, not just helpers

### Read

* **Medium article**: [When Claude Code Skills talk to each other](https://medium.com/@christian.dussol/when-claude-code-skills-talk-to-each-other-f9094d78cb32)
* **GitHub**: [github.com/christian-dussol-cloud-native/kyverno/tree/main/skills](https://github.com/christian-dussol-cloud-native/kyverno/tree/main/skills)
