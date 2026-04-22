# Antidote Reasoning Framework

Antidotes in the failure-patterns file are written in one context. The user's current situation is another context. These rarely line up perfectly.

This reference guides the reasoning step: how to decide whether an antidote applies as written, needs adaptation, or should be overridden.

## Core principle

An antidote is a **hypothesis about what to do instead**, informed by past failures. It is not a rule. Your job is to test the hypothesis against the current facts before handing it to the user.

## Three possible verdicts

### 1. Antidote applies as written

The current situation shares the same structural features as the historical cases that created the pattern. The antidote translates directly.

Example: the user says "I'll pay for a LinkedIn Ads subscription before I have my first validation signal." The pattern "cold outbound dependency" fires, the antidote ("no paid cold channel before one organic signal") applies verbatim. Translate into a specific action: "Before paying for LinkedIn Ads, get one organic signal — an inbound DM, a referral, a newsletter reply. The paid channel comes after.".

### 2. Antidote applies in spirit but needs adaptation

The pattern is real here, but the specific antidote phrasing was written for a different flavor of the same mistake. You keep the underlying principle and restate it for this specific case.

Example: the antidote for "short-burst content" says "4-week consistency proof before monetizing." But the user is not talking about content, they're talking about daily cold calls. The underlying principle (prove sustainability before committing a downstream dependency) still applies. Translate: "Prove 4 weeks of daily cold calls sustained before building the business model around them.".

### 3. Antidote does not apply

The surface-level match to the pattern is real, but the structural features that made past cases fail are absent here. The antidote was written for a world that no longer exists (tool or skill change), or the user has already satisfied the antidote's precondition in a way the file does not capture.

Example: the pattern "never converted to international clients" fires because the user said "let's go after French clients." But the user is specifically running a 30-day French-market experiment to validate a thesis, with a written plan to pivot to US if validated. The antidote ("require 1 paying international client before scaling") does not block this — the context is a time-boxed experiment, not a scaling decision.

When the verdict is "does not apply," say so. Tell the user the pattern matched the surface, but reasoning shows it does not apply in this specific case, and explain why. Do not bury the non-match in silence — the user needs to see that you checked.

## The three questions to ask

Before issuing any verdict, answer these three:

1. **Do the structural features match?** What made the historical cases fail? Are those same features present in the current plan? If yes, proceed. If no, flag the non-match.
2. **Has the environment changed?** Was the antidote written in a context (tools, skills, network, economics) that no longer describes the user's reality? If yes, adapt or override.
3. **Is the antidote's precondition already met?** Sometimes the user has already done the work the antidote demands, just not in a form the file recognizes. Check.

## When multiple patterns conflict

If two patterns match the same plan but their antidotes point in different directions, surface the conflict. Do not pretend the file gives a clean answer when it does not.

Example: pattern A says "move fast, ship now." Pattern B says "don't commit before validation." If both fire, the user has to make a judgment call, not you. Frame the tension, ask which they want to weight more, continue.

## What NOT to do

- Do not improvise new antidotes. If the match is unclear, say so. Do not invent a fifth pattern the user never wrote down.
- Do not steelman the user's plan past the antidote. If the pattern fires and the antidote applies, hold the line. The point of this skill is to save the user from themselves at their most enthusiastic.
- Do not skip the reasoning. Surfacing a pattern without reasoning is just nagging.
