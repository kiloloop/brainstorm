# Brainstorm

**Turn your AI agent into a brainstorm coordinator.**

Protocol, examples, and templates for structured multi-model brainstorming — get better decisions by leveraging model diversity instead of relying on a single perspective.

## Why

Every AI model has blind spots. Claude is great at nuanced reasoning but can miss implementation risks. Codex excels at concrete examples but may overlook strategic implications. Gemini brings unconventional framings that neither surfaces.

When you ask one model, you get one perspective. When you ask three and synthesize, you get something none of them would have produced alone.

We've run dozens of structured brainstorms across a range of decision topics using this protocol. In every case, the multi-model synthesis surfaced insights that any single model missed:

- A naming brainstorm where one model caught a package registry conflict that would have blocked launch
- A competitive analysis where different models found different competitors — the union was the complete picture
- A product strategy brainstorm where one model's framing ("hide the protocol, sell the workflow") became the core positioning

## How It Works

The protocol has three steps:

### 1. Dispatch
Send the same question to 2-3 AI agents with different underlying models.

### 2. Direct
Work hands-on with each agent between rounds. Steer one toward depth, push another toward concrete examples, ask a third to focus on competitive data. This isn't fire-and-forget — it's running simultaneous conversations with advisors who each have different expertise.

### 3. Synthesize
Take the best from each output, resolve contradictions, and produce a synthesis that captures the full picture.

The **interactive direction** step is what makes this different from side-by-side model comparison tools. You're not just parallelizing — you're collaborating with each model based on its strengths.

## Getting Started

### Manual (no tools required)
1. Read the [protocol doc](docs/protocol.md) — full step-by-step guide
2. Browse the [examples](examples/) — real brainstorm results with commentary
3. Pick a [template](templates/) for your decision type
4. Run your first brainstorm with whatever AI tools you already have

For larger research projects, see the [Multi-Agent Research Runbook](docs/multi-agent-research-runbook.md) — a full playbook for angle-splitting, parallel dispatch, synthesis, and signoff.

### With OACP (automated dispatch)
If you use [OACP](https://github.com/kiloloop/oacp) for agent coordination, the brainstorm skill automates dispatch and tracking. See the [protocol doc](docs/protocol.md) for setup.

## Examples

*Coming soon — real brainstorm case studies designed for public sharing.*

Browse the [templates](templates/) to get started with your own brainstorm.

## When to Use Multi-Model Brainstorm

**Good fit:**
- Architecture decisions with genuine tradeoffs
- Naming (models have different aesthetic sensibilities)
- Competitive analysis (different training data = different knowledge)
- Strategy and positioning (diverse framings surface options)
- Pricing (different reasoning about value and anchoring)

**Not needed:**
- Questions with a known correct answer
- Simple code generation
- Tasks where speed matters more than thoroughness

## Project

Brainstorm is part of the [Kiloloop](https://kiloloop.com) open-source ecosystem for multi-agent coordination.

- [OACP](https://github.com/kiloloop/oacp) — Open Agent Coordination Protocol
- [oacp-skills](https://github.com/kiloloop/oacp-skills) — Skill library for OACP
- [agent-estimate](https://github.com/kiloloop/agent-estimate) — AI agent effort estimation

## License

Apache-2.0
