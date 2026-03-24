# Template: Competitive Analysis Brainstorm

## Prompt Template

```
## Our Product
[Brief description of what you're building]

## Competitors to Analyze
- [Competitor 1 — URL, brief description]
- [Competitor 2 — URL, brief description]
- [Or: "Find competitors in [space]"]

## What I Need
For each competitor:
1. What they do well (be specific — features, not vibes)
2. What they do poorly or don't do at all
3. Their pricing model and who pays
4. Their moat (what's hard to replicate)
5. Where we're stronger and where we're weaker
6. One thing we should steal (a feature, a framing, a GTM move)

## Output Format
Comparison table + 1-paragraph narrative per competitor + overall positioning recommendation.
```

## Direction Patterns

| After R1... | Direct to... |
|-------------|-------------|
| Agent missed a major competitor | "Also look at [X]. How do they compare?" |
| Analysis is feature-list only | "Go beyond features. What's their business model? Who funds them? What's their trajectory?" |
| Agent was too generous to competitors | "Be harsher. What's genuinely broken about their product? Read their GitHub issues." |
| Agent was too dismissive of competitors | "Steel-man them. Why would a smart developer choose them over us?" |

## Why Multi-Model Matters Here

Different models have different training data — they literally know about different companies and products. In one competitive analysis:
- Model A found a well-funded competitor that Models B and C didn't know about
- Model B had more current information about pricing changes
- Model C found community sentiment on social media that the others missed

The union of their knowledge is strictly larger than any individual model's.

## Synthesis Focus

1. **Competitor union** — combine all competitors found across agents, don't just pick one list
2. **Threat assessment** — classify each as Low/Medium/High based on overlap and trajectory
3. **Stolen ideas** — the "one thing to steal" from each agent often surfaces different features
