# Multi-Agent Research Runbook

Reusable playbook for dispatching parallel research to multiple agents, synthesizing results, and getting signoff. Used for research reports, brainstorms, architecture decisions, and audits.

**Audience**: Anyone coordinating multiple AI agents for research or decision-making.

---

## When to Use

- Research questions that benefit from multiple perspectives (ecosystem analysis, tool evaluation, feasibility studies)
- Brainstorms where diversity of opinion matters (naming, architecture, strategy)
- Audits where coverage matters more than speed (OSS readiness, security, compliance)
- Any task where a single agent's blind spots could lead to missed insights

**Don't use for**: Implementation tasks, simple lookups, tasks where one agent is clearly sufficient.

---

## Pattern

```
1. Scope & angle-split
2. Dispatch N agents (parallel, complementary angles)
3. Collect artifacts
4. Synthesize into single doc
5. Send synthesis back for signoff review
6. Incorporate feedback, finalize
```

---

## Step 1: Scope & Angle-Split

Define the research question, then carve **complementary angles** — not duplicate scope. Each agent should cover different ground with minimal overlap.

### Angle-splitting strategies

| Strategy | When to use | Example |
|----------|-------------|---------|
| **By depth layer** | Technical topics with ecosystem + implementation + design dimensions | Claude: architecture/ecosystem, Codex: practical setup/deployment, Gemini: design/UX/visual |
| **By source type** | Broad research needing diverse inputs | Claude: docs/papers, Codex: code/repos, Gemini: web/visual |
| **By opinion** | Decision-making, brainstorms | Each agent gives independent recommendation with rationale |
| **By coverage zone** | Audits, large-scope reviews | Split by file set, subsystem, or domain area |

### How many agents?

| Agents | When |
|--------|------|
| 2 | Focused research with clear split (e.g., research vs implementation) |
| 3 | Standard research — covers ecosystem, implementation, and design/UX |
| 3+ with rounds | Deep brainstorms — R1 independent, R2 react to others, R3 converge |

---

## Step 2: Dispatch

Send each agent a structured task with their assigned angle. If using [OACP](https://github.com/kiloloop/oacp), dispatch via inbox protocol. Otherwise, open separate sessions and paste the prompt.

### Dispatch checklist

- [ ] **Output format specified**: What you want back (report, runbook, recommendation)
- [ ] **Angle clearly stated**: What this agent should cover vs what others are covering
- [ ] **Context shared**: Why you're researching, what decisions this informs
- [ ] **Format guidance**: Runbook (actionable steps) vs report (analysis) vs opinion (recommendation)

### Message template

```
## Task
[1-2 sentence summary]

## What to cover
[Numbered list of topics — specific to this agent's angle]

## Context
[What this research is for, what decisions it informs, what other agents are covering]

## Format
[Runbook / report / opinion — specify structure expectations]
```

---

## Step 3: Collect Artifacts

Wait for all agents to complete.

**Quality check before synthesis**:
- Did each agent stay within their assigned angle?
- Are there factual contradictions between reports? (Flag for resolution)
- Did any agent miss key areas from their scope?

---

## Step 4: Synthesize

Combine reports into a single document:

```markdown
# [Topic] — Synthesized Report

*Sources: Agent A research, Agent B research, Agent C research*

## [Section 1]
[Best content from whichever agent covered this best, with additions from others]

## [Section N]
...

## Disagreements & Open Questions
[Where agents disagreed — present both views, recommend resolution]

## Appendix: Agent-Specific Insights
[Unique findings from each agent that didn't fit the main structure]
```

### Synthesis principles

1. **Best source wins** — don't average; pick the most concrete/actionable version
2. **Flag contradictions** — don't silently resolve; present both and recommend
3. **Preserve unique insights** — if only one agent caught something valuable, keep it
4. **Cut redundancy** — don't repeat the same point from 3 angles

---

## Step 5: Signoff Review

Send the synthesis back to all agents for review.

**What to ask for**:
- Factual errors in the synthesis
- Misrepresentation of their research
- Missing insights that were in their report but dropped in synthesis
- Overall quality assessment

**Signoff threshold**: All agents LGTM or issues addressed. One round is usually sufficient.

---

## Step 6: Finalize

Incorporate signoff feedback and finalize the document. The synthesis is now the authoritative output — individual agent reports become supporting artifacts.

---

## Real-World Usage

This runbook has been used in production across dozens of multi-agent research sessions:

| Topic Type | Agents | Rounds | Outcome Pattern |
|-----------|--------|--------|----------------|
| Product feasibility | 3 | 2 + signoff | All agents endorsed → decision made |
| Product vision review | 3 | 1 | Consensus "Needs Work" → 15 specific revisions identified |
| Company naming | 3 | 3 | Winner emerged through progressive narrowing |
| Strategy review | 3 | 1 | 3/3 approved with minor feedback |
| Security audit | 3 | 1 | 3 independent runbooks → merged comprehensive plan |
| OSS naming | 3 | 3 | Package conflict caught in R2 that would have blocked launch |
| Architecture research | 2-3 | 2 | Research → synthesis → 2-round signoff |

The consistent pattern: multi-agent research produces more comprehensive outputs than any single agent. The synthesis step — not the parallel dispatch — is where the value concentrates.
