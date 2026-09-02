# Episode 2: AGENTS.md

### **A README for agents**

A coding agent can work out your language, your tooling, your naming patterns and where the tests live. What it cannot work out is **why**: why that build command and not the obvious one, why that directory is never edited by hand, why one module must not import from another when nothing stops it.

AGENTS.md is where a repository writes that down.

This episode is in two halves. The first is the format. The second is the evidence, **and the evidence is not uniform.**

<figure><img src="../../.gitbook/assets/1 (11).png" alt=""><figcaption></figcaption></figure>

### Part one: the format

A Markdown file at the root of your repository. No schema, no frontmatter, no tooling. Nothing is required: no mandatory headings, no fixed order. The specification suggests a project overview, build and test commands, code style, testing instructions and security considerations. **Suggestions, not obligations.**

What makes it worth having is that it is shared. Codex, Cursor, Copilot, goose and twenty-plus other tools read the same file. Without a common format, each tool asks for its own. A large repository can carry one per package: the OpenAI Codex repository currently has 88.

The format spread before it was standardised. In December 2025 OpenAI donated it to the Agentic AI Foundation, under the Linux Foundation, alongside Anthropic's MCP and Block's goose. MIT licensed, community-governed, and used across more than 60,000 repositories.

📎 **See it**: [AAIF Project Focus: AGENTS.md carousel (PDF)](https://github.com/christian-dussol-ai-native/AGENTS.md/blob/main/carousel/AAIF%20Project%20Focus%20-%20AGENTS.md.pdf), an 11-slide introduction that assumes no prior exposure to agentic coding tools

### Part two: what the evidence says

The interesting question is not what the format is, but whether it works. Two peer-reviewed studies reached conclusions that look opposite, and reading them together is more instructive than either alone.

* **The efficiency study.** Lulla et al., presented at the ICSE Journal Ahead Workshop 2026. A clean paired experiment: ten repositories, 124 pull requests, agents run with and without an AGENTS.md, everything else held constant. Median runtime lower by 28.64%, median output tokens lower by 16.58%, with comparable task completion
* **The correctness study.** Gloaguen et al., ETH Zurich and LogicStar.ai, at the ICLR 2026 Workshop on Memory for LLM-Based Agentic Systems. Different design, and their finding is that context files do not generally improve task success rates while increasing inference cost by over 20% on average
* **They are not measuring the same thing.** Lulla measures how long the agent takes and how many tokens it burns. Gloaguen measures whether the agent solves the task. **An agent can navigate a codebase faster without arriving at a better answer.** The cost figures are not counted the same way either
* **Two later papers take up the reconciliation directly**, and point at the step budget and the task difficulty as part of what separates the two results

#### Where they agree

On the one question that matters when you sit down to write the file. Agents follow the instructions they are given. Repository overviews, common and recommended though they are, do not show the same benefit.

The AAIF's own guide turns this into a test you can apply to every line: **would knowing this change what the agent does?** "Follow good practices" fails it. "Run `pnpm test` before opening a PR" passes it.

#### What I take from it

The format is simple, portable across tools and now governed. That much is settled. Whether it improves outcomes is not, and the honest position is that **it depends on what you write and what you measure.**

Gloaguen's closing recommendation is the one I would keep: any attempt to improve performance should be rigorously evaluated before deployment. In a regulated environment, that phrasing is familiar. **It is the difference between a practice you adopted and a practice you can defend.**

→ **Read it**: [Medium](https://medium.com/@christian.dussol/a-readme-for-agents-what-agents-md-is-and-what-the-evidence-says-15ef5f935740)

→ **Browse it**: [AGENTS.md](https://github.com/christian-dussol-ai-native/AGENTS.md) on GitHub, a resource repository with nothing to install and nothing to run

***

MCP governs what an agent may do. AGENTS.md tells it how this project works. Capability and context are different problems, solved by different artifacts.

Next in the series: goose, the harness that runs the agent.
