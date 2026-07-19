---
description: >-
  What Claude Code Skills are, how they compose, and what they reveal about the
  architecture of AI agents. Five parts, from understanding to governance.
---

# From Prompts to Packages

Skills are a format for packaging reusable AI capabilities, a `SKILL.md` file plus supporting references that Claude loads on demand. But the format itself isn't the point. The point is what Skills enable: a way to package expertise rather than copy-paste prompts, a way to compose AI capabilities like we compose software, and a glimpse of how AI agents will be governed when they stop being demos and start being infrastructure.

The series follows a deliberate progression. Each part unlocks a capability the previous one could not show.

Part 1: Understand → What a Skill is\
Part 2: Generate → A Skill produces code\
Part 3: Compose → A Skill calls another Skill\
Part 4: Connect → A Skill reaches the real world via MCP\
Part 5: Govern → Skills as a foundation for AI governance

[**Part 1: How Claude Code Skills Work**](part-1-how-claude-code-skills-work.md)**.** What a Skill actually is. Anatomy (`SKILL.md`, frontmatter, progressive disclosure), invocation flow, and where Skills sit in the four-layer framework of AI agents. _Skills are to AI agents what Helm Charts are to Kubernetes deployments._

[**Part 2: Building a Real Skill: kyverno-policy-generator**](part-2-building-a-real-skill-kyverno-policy-generator.md)**.** A Skill can generate. From zero to a production-ready Skill that produces validated, tested Kyverno policies. The shift from copy-pasting prompts to packaging expertise.

[**Bonus, 6 Principles from Anthropic's Official Skills Guide**](bonus-6-principles-from-anthropics-official-skills-guide.md)**.** _(Method.)_ Part 2 showed the result. This one shows how it was built. Anthropic published a complete guide for building Skills, and six of its principles shaped every design decision in `kyverno-policy-generator`. Some were intuitive. Others changed the approach entirely.

[**Part 3: When Skills Talk to Each Other**](part-3-when-skills-talk-to-each-other.md)**.** A Skill can audit, and Skills can call each other. The `kyverno-policy-auditor` runs an 8-dimension audit and triggers the generator when it detects gaps. Skills are not tools. They are an ecosystem.

[**Part 4: Connecting Skills to the Real World via MCP**](part-4-connecting-skills-to-the-real-world-via-mcp.md)**.** A Skill can reach beyond Claude. A FinOps Skill that pulls real cost data via MCP, analyzes it, and triggers governance actions. The full loop: data → analysis → action.

[**Part 5: Skills as a Foundation for AI Governance**](part-5-skills-as-a-foundation-for-ai-governance.md)**.** What I learned from building the series. Skills as one of the answers to the question every platform engineer is starting to ask: _how do we govern AI agents when they stop being demos and become infrastructure?_ The bridge to CNCF Arc 3 (KAgent, KServe, KGateway)

All code is open source under the [https://github.com/christian-dussol-cloud-native/kyverno/tree/main/skills](https://github.com/christian-dussol-cloud-native/kyverno/tree/main/skills) repository, licensed CC BY-SA 4.0. The experiments are public and the things that didn't work are part of the record.

> _AI scales what you know. It doesn't replace what you learned._
