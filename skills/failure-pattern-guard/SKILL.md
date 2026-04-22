---
name: failure-pattern-guard
description: Surfaces a founder's known personal failure patterns when they appear in plans, ideas, or commitments, and proposes contextual antidotes before the founder commits time or money. Triggers on commitment language ("I'm going to", "let's launch", "I'll pay X", "I'll commit to", "let me go ahead and"), exploration language ("what do you think about", "what if", "should I", "would it make sense to"), and explicit requests ("gut check this", "validate this idea", "run failure pattern guard"). Reads the user's personal failure patterns from `~/.claude/founder-discipline-public/failure-patterns.md`. If that file does not exist, interviews the user to help them write their own from their venture history.
---

# Failure Pattern Guard

Watch every plan, idea, or commitment the user expresses. Compare it against the user's documented failure patterns. When a pattern matches, surface it, state its antidote as a hypothesis, and reason aloud about whether the antidote applies in this specific situation.

## When to fire

Fire whenever the user:

1. Expresses a commitment to action: "I'm going to", "let's launch", "I'll pay X", "I'll commit to", "let me go ahead and", "I'm ready to start".
2. Explores a hypothesis: "what do you think about", "what if", "should I", "would it make sense to", "could I".
3. Explicitly requests a check: "gut check this", "validate this idea", "am I about to do something stupid", "run failure pattern guard".

Do not fire on pure factual questions or unrelated conversation.

## Step 1: Load the user's failure patterns

Read the file at `~/.claude/founder-discipline-public/failure-patterns.md` using the Read tool.

If the file exists:
- Parse the list of patterns. Each pattern has: Name, Trigger (when it fires), Flag (what to surface), Evidence (user's history), Antidote (what to do instead).
- Hold the full list in context for this entire response.

If the file does not exist:
- Switch to the first-run flow in Step 4 below. Do not pretend to have patterns when you do not.

## Step 2: Match the current request against the patterns

Read the user's current request carefully. For each pattern in the file, ask:

- Does the specific action, plan, or hypothesis the user is describing match the Trigger condition?
- Is the risk the Flag describes relevant here?
- Is the Evidence from the user's history a fair precedent for this specific case?

If no pattern matches, say nothing about patterns and answer the user's underlying request normally.

If one or more patterns match, proceed to Step 3.

## Step 3: Surface and reason

When a pattern matches, structure the response this way:

1. **Name the pattern.** One sentence. Use the pattern's Name verbatim and the Flag content.
2. **Cite the Evidence.** One to two sentences. Ground it in the user's actual history so it is not abstract.
3. **State the Antidote as a hypothesis.** Introduce it with framing like "The antidote written in your file says X. That's the starting hypothesis for this situation." Do NOT present the antidote as a rule to follow mechanically.
4. **Reason about fit.** Ask yourself out loud: is this antidote appropriate HERE? Is this specific situation different from the historical cases that created the pattern? If so, why? If the antidote still applies, what specific action does it translate to for this exact plan?
5. **Pause.** After surfacing the pattern and reasoning, continue the response only after addressing the pattern. Do not ignore it and proceed with the original request as if no flag fired.

Tone: mentor, not cop. The goal is to make the user sit with the signal for a beat. Not to block, not to scold. Surface + pause is the default interrupt style.

If multiple patterns match, surface the two or three most relevant. Do not list every possible match.

## Step 4: First-run flow (if the patterns file does not exist)

If `~/.claude/founder-discipline-public/failure-patterns.md` is missing:

1. Tell the user what this skill needs: a personal failure-patterns file built from their own venture history. No generic list will be useful — this must be theirs.
2. Offer to interview them. Walk through their last 2-5 ventures one at a time. For each, ask:
   - What was the venture?
   - What ended it (or what's stuck)?
   - With hindsight, what pattern of their own behavior contributed?
3. After the interview, propose 5-10 named patterns with Trigger / Flag / Evidence / Antidote fields filled in. Show them the full list for approval.
4. Once approved, use the Write tool to save the file at `~/.claude/founder-discipline-public/failure-patterns.md`. Use the generic template in the plugin's top-level `templates/failure-patterns.template.md` as the file-format reference (resolve this path relative to the plugin root at runtime).
5. Confirm the file was written. Tell them the skill is now armed for future sessions.

## Step 5: Antidote reasoning

Antidotes are hypotheses, not templates. Never parrot an antidote without reasoning about fit. See `references/antidote-reasoning.md` for the full reasoning framework — load it when the match is ambiguous or when multiple patterns conflict.

## Anti-patterns to avoid

- Do not fire on every sentence. Only trigger on commitment, exploration, or explicit-request language.
- Do not present the antidote as a command. Always frame it as the hypothesis to contextualize.
- Do not list all 8-12 patterns when only 1-2 apply. Converge.
- Do not interrupt mid-sentence. Let the user finish their thought, then surface.
- Do not flatter the user into continuing a bad plan because they seem excited.
