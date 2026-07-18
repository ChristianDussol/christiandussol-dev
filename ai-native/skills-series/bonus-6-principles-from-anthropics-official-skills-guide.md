---
description: >-
  The six principles from Anthropic's official Skills guide, applied to a real
  production Skill rather than a toy example. The method behind the series.
---

# Bonus: 6 principles from Anthropic's official Skills guide

### Method: how I actually built it

Part 2 showed the result. This bonus episode shows how I got there. Anthropic published a complete guide for building Skills, and I followed it closely while building `kyverno-policy-generator`. Six principles shaped every design decision. Some were intuitive. Others changed my approach fundamentally. They apply to any Skill, not just this Kyverno use case.

<figure><img src="../../.gitbook/assets/1 (8).png" alt="" width="563"><figcaption></figcaption></figure>

### What the article covers

* **The description field decides everything.** It is not documentation for humans, it is a routing instruction for Claude. Write it like a load balancer rule, and include the negative triggers
* **Progressive disclosure is lazy loading.** Three levels: metadata always loaded, SKILL.md body on trigger, references on demand. It saves the most precious resource Claude has
* **Scripts for deterministic validation, not instructions.** Code is deterministic, language interpretation isn't. Instructions are for guidance, scripts are for enforcement
* **Concrete examples in SKILL.md are training data, not documentation.** They show Claude the reasoning chain, not just the output format
* **No README.md inside the Skill folder.** SKILL.md is the brain. Everything else is supporting material, and ambiguity between the two costs you
* **Test triggering before testing execution.** If your Skill produces poor results, check triggering first. A Skill that activates on the wrong prompts will always produce poor results

### Read

* **Medium article**: [6 Principles from Anthropic's Official Skills Guide: Applied to a real Skill](https://medium.com/@christian.dussol/6-principles-from-anthropics-official-skills-guide-applied-to-a-real-skill-d59424e38ff3)
* **GitHub**: [github.com/christian-dussol-cloud-native/kyverno/tree/main/skills](https://github.com/christian-dussol-cloud-native/kyverno/tree/main/skills)
* **Anthropic's guide**: [The Complete Guide to Building Skills for Claude](https://claude.com/blog/complete-guide-to-building-skills-for-claude)
