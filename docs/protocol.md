# How to Run a Multi-Agent Brainstorm

A step-by-step protocol for structured decision-making using multiple AI models.

## Prerequisites

- Access to 2-3 AI agents with different underlying models (e.g., Claude Code + Codex + Gemini)
- A decision or question that benefits from diverse perspectives
- 30-60 minutes for a single-round brainstorm, 60-90 minutes for multi-round

## The Protocol

### Step 1: Frame the Question

Write a clear, specific prompt. The same prompt goes to all agents. Good brainstorm prompts:

- State the decision context and constraints
- Ask for a specific deliverable (not "what do you think?" but "propose 3 approaches with tradeoffs")
- Include relevant data and background
- Set output format expectations

**Example:**
```
We're naming our open-source protocol for multi-agent coordination.
Constraints: must be available on PyPI, GitHub, and as a domain.
Current working name: "coordination-core" (too long, too generic).
Audience: developers who use AI coding agents.

Propose 10 names with rationale. For each, note: memorability,
domain availability likelihood, and positioning signal.
```

### Step 2: Dispatch to Multiple Agents

Send the same prompt to 2-3 agents. Each agent should work independently — they should not see each other's outputs in round 1.

**Manual dispatch:**
- Open separate sessions in each AI tool
- Paste the same prompt
- Let each agent complete its response

**With OACP:**
```bash
oacp send <project> --from you --to claude --type task_request \
  --subject "Brainstorm: [topic]" --body-file prompt.md
oacp send <project> --from you --to codex --type task_request \
  --subject "Brainstorm: [topic]" --body-file prompt.md
oacp send <project> --from you --to gemini --type task_request \
  --subject "Brainstorm: [topic]" --body-file prompt.md
```

### Step 3: Direct (the key step)

This is what separates structured brainstorming from fire-and-forget parallel dispatch.

After receiving initial outputs, **work with each agent individually**:

- **Deepen strengths**: If Agent A gave a great framework but weak examples, ask for concrete examples
- **Explore angles**: If Agent B mentioned a risk nobody else saw, ask it to elaborate
- **Redirect**: If Agent C went off-topic, redirect toward the specific decision
- **Cross-pollinate** (round 2+): Share interesting insights from one agent with another: "Agent A suggested X — what's wrong with that approach?"

**Direction patterns by agent type:**

| Agent strength | Direction to give |
|----------------|------------------|
| Strong on reasoning | "Give me concrete implementation risks" |
| Strong on examples | "Now step back — what's the strategic framing?" |
| Strong on breadth | "Go deep on your top 2 recommendations" |
| Produced shallow output | "This is too high-level. Give me specifics, sources, and tradeoffs" |

### Step 4: Synthesize

After 1-3 rounds of dispatch and direction, synthesize:

1. **Collect key insights** from each agent — what did each uniquely contribute?
2. **Resolve contradictions** — where agents disagree, which reasoning is stronger?
3. **Identify blind spots** — what did nobody mention? What assumptions went unquestioned?
4. **Write the synthesis** — a single document that captures the best from each, attributes sources, and states the decision or recommendation

**Synthesis template:**
```markdown
## Decision: [topic]

### Summary
[1-2 sentence recommendation]

### Key Insights by Source
- **Agent A**: [unique contribution]
- **Agent B**: [unique contribution]
- **Agent C**: [unique contribution]

### Where They Agreed
[consensus points — these are likely strong signals]

### Where They Disagreed
[divergent points — these are where the real decision lies]

### Blind Spots Identified
[what nobody mentioned that should have been considered]

### Decision
[final recommendation with rationale]
```

## Patterns

### Single Round (30 min)
Best for: factual research, competitive scans, brainstorming options.
- Dispatch same prompt to 3 agents
- Read outputs
- Synthesize

### Two Rounds with Direction (60 min)
Best for: strategic decisions, architecture choices, positioning.
- R1: Dispatch same prompt to 3 agents
- Review R1 outputs, identify strengths and gaps
- R2: Send directed follow-ups to each agent based on what R1 revealed
- Synthesize R1 + R2

### Three Rounds with Signoff (90 min)
Best for: high-stakes decisions, naming, pricing, go/no-go.
- R1: Broad brainstorm
- R2: Directed deep-dives based on R1
- R3: Present synthesis to all agents for final review/signoff
- Finalize

## Tips

- **2 agents is often enough.** Don't add a third model just for completeness. Two strong perspectives with good direction beats three shallow ones.
- **The synthesis is where the value concentrates.** Raw agent outputs are long. The synthesis should be 5:1 shorter and capture only what matters.
- **Model diversity > model quality for brainstorms.** A mix of Claude + Codex + Gemini surfaces more diverse insights than 3 Claude sessions, even though Claude may be "better" on average.
- **Interactive direction is the skill.** You get better at this with practice. Your first brainstorm will feel clunky. By your fifth, you'll have intuitions about which model to push in which direction.
- **Not everything needs a brainstorm.** If there's a clear right answer, just ask one model. Brainstorms are for genuine uncertainty — decisions where blind spots matter.
