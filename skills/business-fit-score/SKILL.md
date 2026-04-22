---
name: business-fit-score
description: Scores a business idea from 0 to 100 against the user's personal criteria and weights. Reads `~/.claude/founder-discipline-public/business-criteria.md`. On first run (missing file), walks the user through all their criteria one by one, validates each weight individually (typically 3x / 2x / 1x or custom), and writes the personalized file. On subsequent runs, silently uses the saved config and outputs a weighted score plus a per-criterion critique. Triggers on "score this idea", "rate this business", "how does this fit my criteria", "is this right for me", "business-fit-score", "run the scorer".
---

# Business Fit Score

Score a proposed business or idea against the user's personal weighted criteria. Output a 0-100 score plus a critique of how the idea performs against each criterion.

## When to fire

Fire whenever the user:

1. Asks for a score: "score this idea", "rate this business", "how does this fit my criteria".
2. Asks for fit evaluation: "is this right for me", "does this align with my criteria", "am I the right founder for this".
3. Explicitly invokes the scorer: "run business-fit-score", "use the scorer".

Do not fire on early-stage brainstorming where the user has not yet articulated a specific idea worth scoring.

## Step 1: Load the user's criteria

Read `~/.claude/founder-discipline-public/business-criteria.md` using the Read tool.

If the file exists: parse the criteria list. Each criterion has: Number, Name, Weight (typically 3x / 2x / 1x), Rationale. The file may also include hard elimination criteria.

If the file does not exist: switch to the first-run flow (Step 5). Do not score using generic criteria.

## Step 2: Check the hard elimination criteria first

Before scoring, run the idea through any hard elimination criteria listed in the file (binary yes/no criteria the user has declared as non-negotiable rejections).

If the idea violates a hard elimination criterion, STOP the scoring process. Tell the user: "This idea violates hard elimination criterion #X: <criterion>. Elaborate scoring is pointless until the idea is reframed to avoid this. Do you want to reframe it, or skip the hard filter for this run?"

If the idea passes all hard eliminations, proceed to Step 3.

## Step 3: Score each criterion

For each criterion in the file:

1. Assess the idea against this specific criterion. Be rigorous. Score as an integer from 1 to 5:
   - 5 = strong match, clear fit
   - 4 = good match, minor gaps
   - 3 = neutral / unclear / mixed evidence
   - 2 = weak match, meaningful gaps
   - 1 = poor match, this is actively misaligned

2. Write a one-sentence justification for the score. Ground it in specifics of the idea, not generalities.

3. Apply the weight: `weighted_score = raw_score × weight`.

## Step 4: Compute and report

- **Total weighted score** = sum of all weighted scores.
- **Max possible score** = sum of (5 × weight) for all criteria.
- **Normalized score (0-100)** = (total weighted / max possible) × 100.

Report in this format:

```
## Business Fit Score: <XX>/100

### Criterion-by-criterion

| # | Criterion | Weight | Raw (1-5) | Weighted | Justification |
|---|-----------|--------|-----------|----------|---------------|
| 1 | <name>    | 3x     | 4         | 12       | <one line>    |
| ... | ...     | ...    | ...       | ...      | ...           |

### Overall
- Total weighted: XX / YY
- Normalized: XX / 100

### Top 3 strengths
1. Criterion <N>: <why this idea scores high here>
2. ...
3. ...

### Top 3 gaps (where this idea breaks down)
1. Criterion <N>: <specific weakness>
2. ...
3. ...

### Verdict
One paragraph. Is this idea a go, a reframe, or a kill — based on the score AND the specific weaknesses. Be honest. Do not soften a low score with hedging.
```

Scoring bands (suggestive, not mechanical):
- **80-100**: Strong fit. The idea passes most criteria with high weights.
- **60-79**: Decent fit with known gaps. Worth pursuing if gaps are addressable.
- **40-59**: Weak fit. Probably needs significant reframing.
- **0-39**: Bad fit. Do not pursue without a major rethink. Consider this a kill signal.

## Step 5: First-run flow (if the criteria file does not exist)

If `~/.claude/founder-discipline-public/business-criteria.md` is missing:

1. Tell the user: "I can't score without knowing your criteria. These should be yours, not generic. Let me help you build the list now."
2. Offer two paths:
   - **Guided interview** (recommended for first use): walk through 10-12 proposed criteria, user approves / adjusts / drops / adds. Each criterion's weight is validated one at a time (3x = must-have, 2x = strongly prefer, 1x = nice-to-have, or custom).
   - **Bring your own**: user pastes or dictates their pre-existing criteria; skill reformats and saves.
3. During the interview, use `references/first-run-interview.md` as the conversation flow.
4. End the interview by drafting the full file contents (criteria + weights + hard eliminations + rationale notes) and showing it for approval.
5. Once approved, use the Write tool to save at `~/.claude/founder-discipline-public/business-criteria.md` following the format in `references/scoring-methodology.md`.
6. Confirm the write. Immediately re-enter Step 1 to score the original idea the user came in with.

## Anti-patterns to avoid

- Do not invent generic criteria. If the file is missing, trigger the interview. Do not improvise.
- Do not bury a low score. If the normalized score is below 60, say so explicitly in the verdict.
- Do not over-reward the weighted math. The score is a signal, not truth. Always read the top-3 gaps out loud.
- Do not skip hard eliminations. Binary rejections come before weighted scoring, always.
- Do not average without showing the per-criterion table. The user needs to see which criteria drove the score.
