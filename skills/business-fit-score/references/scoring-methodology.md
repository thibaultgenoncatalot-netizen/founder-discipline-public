# Scoring Methodology and File Format

## business-criteria.md — File Format

Located at `~/.claude/founder-discipline-public/business-criteria.md`. This file is personal and lives globally (applies across any Claude surface the user opens).

```markdown
# Business Criteria

> Personal weighted criteria for evaluating business ideas.
> Last updated: YYYY-MM-DD

## Weighted Criteria

| # | Criterion | Weight | Rationale |
|---|-----------|--------|-----------|
| 1 | <name>    | 3x     | <why this matters to me> |
| 2 | <name>    | 2x     | <why this matters to me> |
| ... | ...     | ...    | ... |

## Hard Elimination Criteria (binary NOs)

Any idea violating one of these is rejected before weighted scoring. Do not proceed to score.

- <elimination criterion 1>
- <elimination criterion 2>
- ...
```

## Weight scale

Standard:
- **3x** = must-have. A low score on this criterion is disqualifying on its own.
- **2x** = strongly prefer. A low score is a red flag but not a veto.
- **1x** = nice-to-have. A low score is acceptable if offset by high scores elsewhere.

Custom weights are allowed (e.g., 4x, 0.5x) but should be rare. Stick to 3/2/1 unless the user explicitly wants a weight outside the scale.

## Scoring math

For each criterion:
- Raw score: integer 1-5.
- Weighted score: `raw × weight`.

Totals:
- **Total weighted** = sum of all (raw × weight).
- **Max possible** = sum of (5 × weight) for all criteria.
- **Normalized (0-100)** = (total weighted / max possible) × 100.

## Interpretation bands

- **80-100**: Strong fit. Pursue, but still write kill criteria.
- **60-79**: Decent fit with addressable gaps. Identify the gaps and plan how to close them BEFORE committing.
- **40-59**: Weak fit. Reframe or consider a different idea.
- **0-39**: Bad fit. Do not pursue without major rethinking.

These bands are heuristics, not rules. A 75 with a 1/5 on a 3x must-have criterion is more concerning than a 65 that's flat across the board. Always read the per-criterion breakdown.

## When criteria need to change

Business criteria should be stable, but not frozen. Update the file when:

- A venture ends and a new lesson emerges about what actually mattered.
- Life circumstances shift (runway, location, health, family) in a way that changes priorities.
- A criterion has been scored consistently 5/5 across all ideas (it's no longer discriminating — either drop it or reweight).
- A criterion has never triggered any meaningful score difference — it may be cosmetic.

Review cadence: every 6 months, or after any venture kill.

## When NOT to trust the score

- If the user is emotionally attached to the idea, the raw scores will be inflated. Watch for this.
- If the idea is too abstract to score, tell the user. "I can't score 'I want to do something in AI' — give me a specific idea." Don't fabricate scores for vague ideas.
- If multiple criteria are effectively measuring the same thing (redundancy), the score gets artificially amplified. Flag this.
