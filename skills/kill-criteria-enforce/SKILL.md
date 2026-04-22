---
name: kill-criteria-enforce
description: Blocks resource commitment on a project until written kill criteria exist for that project. Reads `kill-criteria.md` from the current project folder. If absent, refuses to proceed with any commitment action and walks the user through writing one (validation signal, anti-signal, review date, accountability partner). Triggers on commitment phrases ("let me pay X", "I'm going to launch", "I'll commit to", "let's start", "I'm ready to invest"), project initialization phrases ("new project", "starting X", "I want to build"), and explicit requests ("enforce kill criteria", "check my kill criteria").
---

# Kill Criteria Enforce

Every new venture, project, or meaningful investment needs written kill criteria before the founder commits time or money. This skill enforces that rule.

## When to fire

Fire whenever the user:

1. Signals commitment on a project: "let me pay for X", "I'm going to launch", "I'll commit to", "let's start", "I'm ready to invest", "let me hire", "let me sign up for".
2. Initializes a new project: "new project", "starting X", "I want to build", "I'm going to work on".
3. Explicitly requests enforcement: "enforce kill criteria", "check my kill criteria", "do I have kill criteria for this".

Do not fire on factual questions, brainstorming, or hypothetical exploration with no commitment language.

## Step 1: Identify the project

Determine which project the user is referring to. Check:

1. The current working directory or project folder the conversation is anchored in.
2. Any project name the user mentioned in the request.
3. The most recently opened or discussed project in the session.

If the project is ambiguous, ask the user to confirm which project this commitment belongs to before proceeding.

## Step 2: Check for kill-criteria.md in the project folder

Use the Read tool to check for `kill-criteria.md` in the project's root folder.

- If the file exists: proceed to Step 3 (Load and reference).
- If the file does not exist: proceed to Step 4 (Block and build).

## Step 3: Load and reference

Read the existing `kill-criteria.md` file. Surface the key contents in the response:

- **Validation signal** (what counts as proof the project is working)
- **Anti-signal** (what would prove it's not working and warrants a kill)
- **Review dates** (when the user has committed to checking in against the criteria)
- **Accountability** (who else holds them to this)

Contextualize the current commitment against the criteria:
- Does the commitment the user is about to make respect or violate the anti-signals?
- Is the user past a review date without having reviewed?
- Is there a validation signal they claimed they'd hit by now that they haven't?

If the criteria are healthy and the commitment is aligned, give a short confirmation ("Your kill criteria for this project are X. This commitment is consistent with them.") and let the user proceed.

If the criteria are violated or stale, flag it explicitly. Do not let the commitment through without the user addressing the gap.

## Step 4: Block and build

If no `kill-criteria.md` exists in the project folder, refuse to proceed with the commitment.

Say something like: "I can't help you commit to this yet — there are no written kill criteria for this project. Writing them is the rule. Let me walk you through it now, and it takes about 5 minutes."

Then interview the user with these four questions, in order:

1. **Validation signal (positive):** What specific, measurable, time-bound outcome would prove this is working? Example: "3 paid customers by Week 12" or "$2,000 MRR by Week 16."
2. **Anti-signal (kill trigger):** What specific outcome would prove it's NOT working and warrant a kill? Example: "Fewer than 1 paid customer by Week 8" or "Zero replies to the first 50 warm-network outreach attempts."
3. **Review dates:** When will the user check progress against these criteria? Typical cadence: Week 4, Week 8, Week 12. At minimum, one mid-point and one end-point.
4. **Accountability:** Who will the user review these with besides themselves? Name a person, a group, or a recurring slot (e.g., "weekly call with a peer mentor on Fridays", "monthly advisor sync"). Self-accountability alone tends to fail.

After the user answers all four, draft `kill-criteria.md` following the format in `references/kill-criteria-template.md` and show it to them for review.

Once they approve, use the Write tool to save the file at `<project-folder>/kill-criteria.md`.

Confirm the file was written. THEN let the commitment proceed — but in the same response, restate the most important kill line so the user leaves with it in their head.

## Step 5: Return to the commitment

After writing (or reading) the kill criteria, circle back to the user's original commitment. Help them with it — but only now, after the discipline gate is passed.

## What the kill-criteria.md file should contain

See `references/kill-criteria-template.md` for the full file format. In brief:

- Project name
- Hypothesis (one sentence — what the user believes this project will achieve)
- Validation signal (positive milestone)
- Anti-signal (kill trigger)
- Review dates (explicit calendar dates, not "monthly")
- Accountability (named person or group)
- Signature line with date

## Anti-patterns to avoid

- Do not accept vague kill criteria ("I'll know it's not working"). Force specificity.
- Do not let the user postpone writing the file. "I'll do it later" is exactly the pattern this skill exists to prevent.
- Do not approve a validation signal that is not measurable (e.g., "feeling good about the project" is not a signal).
- Do not accept self-only accountability without flagging it. External accountability is the discipline multiplier.
- Do not silently proceed if the file is present but stale. Flag review dates that have passed.
