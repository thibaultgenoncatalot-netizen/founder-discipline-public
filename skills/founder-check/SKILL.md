---
name: founder-check
description: Meta-skill that runs the full founder-discipline audit on a business idea or plan. Executes failure-pattern-guard, kill-criteria-enforce, and business-fit-score in sequence, then synthesizes one coherent verdict. Triggers ONLY on explicit user commands. Does not fire automatically. Triggers: "run founder check", "full audit", "am I about to do something stupid", "founder-check", "do the full discipline audit", "gut check me".
---

# Founder Check

Run the complete founder-discipline audit. This skill orchestrates the other three skills and delivers a single synthesized verdict.

## When to fire

Fire ONLY on explicit user commands. This skill does NOT trigger automatically on commitment or exploration language — only on direct invocation.

Valid triggers:
- "run founder check"
- "full audit"
- "am I about to do something stupid"
- "founder-check"
- "do the full discipline audit"
- "gut check me"
- "run everything"

If the user uses commitment or exploration language without an explicit founder-check invocation, the individual skills (`failure-pattern-guard`, `kill-criteria-enforce`, `business-fit-score`) will fire on their own if appropriate. Do not fire `founder-check` as a catch-all.

## Step 1: Confirm scope

When invoked, confirm what the user wants checked:

> "Running the full founder-discipline audit. Confirm what I'm auditing: <restate the idea or plan in one sentence>. Correct?"

If the user has not clearly articulated what to check, ask:

> "What specifically do you want audited? A business idea, a commitment you're about to make, a pivot you're considering?"

Do not proceed without a crisp subject.

## Step 2: Run failure-pattern-guard

Invoke the logic of the `failure-pattern-guard` skill:

1. Load `~/.claude/founder-discipline-public/failure-patterns.md`.
2. Match the current plan/idea against every pattern.
3. Surface all matches (not just 1-2 like in the standalone skill — this is a full audit).
4. For each match, state the antidote as a hypothesis and reason about fit.

Capture the output for synthesis in Step 5.

## Step 3: Run kill-criteria-enforce

Invoke the logic of the `kill-criteria-enforce` skill:

1. Identify the project folder for this plan.
2. Check for `kill-criteria.md` in that folder.
3. If present: surface the criteria and flag any violations or stale reviews.
4. If absent: do NOT interrupt the audit to run the full interview flow. Instead, note it as a gap and continue. The user can fix the gap after the full audit completes.

> **Design note (intentional softening):** standalone `kill-criteria-enforce` would refuse to proceed on a missing file and block any commitment action. Here, `founder-check` deliberately relaxes that gate — the meta-skill's contract is "deliver ONE coherent verdict", not "interrupt three times". The absence of `kill-criteria.md` is reported as a gap in Step 5's synthesis and should surface as a blocker in the verdict when the hardest-to-hear finding demands it. If you run `founder-check` instead of the individual skills, you are opting into this softer flow by choice. To retain the hard gate, invoke `kill-criteria-enforce` directly instead of `founder-check`.

Capture the output for synthesis in Step 5.

## Step 4: Run business-fit-score

Invoke the logic of the `business-fit-score` skill:

1. Load `~/.claude/founder-discipline-public/business-criteria.md`.
2. Check hard elimination criteria first.
3. If the idea survives, score each weighted criterion, compute the normalized 0-100 score, and identify top 3 strengths and top 3 gaps.
4. If the idea violates a hard elimination, note it and skip the weighted scoring.

Capture the output for synthesis in Step 5.

## Step 5: Synthesize into one verdict

Do not just concatenate the three outputs. Synthesize them. Ask:

- **Do the three skills agree?** If pattern-guard says "this is execution-before-validation" AND the fit score is 85/100, the fit score might be misleading — the pattern is telling you the execution timing is wrong even if the idea is right.
- **What is the DOMINANT signal?** A low fit score (<50) dominates. A hard elimination violation dominates. A fired failure pattern with a clear evidence match dominates.
- **What is the single hardest-to-hear finding?** Lead with it.

Report in this format:

```
# Founder Check Verdict: <ONE WORD — GO / REFRAME / PAUSE / KILL>

## The hardest-to-hear finding

One paragraph. The single most important thing the user needs to sit with from this audit.

## Failure patterns triggered

<Number fired> patterns. Brief list with name + specific match.

## Kill criteria status

Either: criteria exist (cite them) OR criteria missing (flag as blocker).

## Business fit score

XX/100. Top 3 strengths. Top 3 gaps.

## Decision framework

What the user should do next. Be specific:
- If GO: confirm kill criteria are written, confirm no patterns are fired, proceed.
- If REFRAME: name the specific reframe ("same idea, different target market" or "same idea, add technical partner first").
- If PAUSE: what needs to be resolved before re-running the audit (e.g., "write kill criteria first" or "validate with 1 paying customer").
- If KILL: why. Do not soften. List the dominant disqualifying signals.

## One sentence summary

The user will remember this line more than any other part of the audit. Make it land.
```

## Extension slot

This skill is a placeholder for orchestrating additional future discipline skills (e.g., runway-check, personal-state-check, etc.). When new skills are added to this plugin, update this SKILL.md to include them in the audit sequence.

## Anti-patterns to avoid

- Do not fire automatically. Only on explicit command.
- Do not skip any of the three component skills. A full audit runs all three, even if one would normally not trigger.
- Do not deliver three separate outputs and call it a verdict. Synthesize.
- Do not soften the verdict if the signals are hard. The whole point of running a full audit is to get the harsh truth in one place.
- Do not produce a 4-page output. Tight, specific, verdict-first. The user is presumably at a decision point — get them to the decision.
