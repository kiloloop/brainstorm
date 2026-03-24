# Template: Architecture Decision Brainstorm

## Prompt Template

```
## Context
[Describe the system, current state, and what's changing]

## Decision
[State the specific architecture decision to be made]

## Constraints
- [Constraint 1]
- [Constraint 2]
- [Budget/timeline/team constraints]

## Options Under Consideration
1. [Option A — brief description]
2. [Option B — brief description]
3. [Open to other approaches]

## What I Need
For each viable approach, provide:
- Architecture diagram (ASCII)
- Tradeoffs (what you gain vs what you lose)
- Implementation complexity (S/M/L)
- Operational burden (what breaks at 2 AM?)
- Migration path from current state
- What kills this approach (the dealbreaker scenario)
```

## Direction Patterns

After R1, direct each agent based on their output:

| If the agent produced... | Direct them to... |
|--------------------------|-------------------|
| Strong theoretical framework | "Give me concrete implementation risks and failure modes" |
| Good technical depth | "Step back — what's the business/operational impact of each option?" |
| Broad but shallow comparison | "Go deep on your top recommendation. What does the migration look like day by day?" |
| Only happy-path analysis | "What breaks? What's the worst-case scenario for your recommended approach?" |

## Synthesis Focus

Architecture decisions benefit most from:
1. **Tradeoff alignment** — which tradeoffs are acceptable given constraints?
2. **Risk union** — combine all risks identified across agents (each catches different failure modes)
3. **Migration realism** — prefer the approach with the clearest migration path, not the prettiest end state
