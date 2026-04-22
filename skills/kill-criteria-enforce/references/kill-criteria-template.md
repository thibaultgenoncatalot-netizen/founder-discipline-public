# kill-criteria.md — File Format Reference

Every project folder enforced by `kill-criteria-enforce` must contain a `kill-criteria.md` file at its root, following this exact structure.

## Template

```markdown
# Kill Criteria: <Project Name>

> Written before committing time or money. Reviewed on the dates below. Violated = kill.

## Hypothesis

One sentence. What you believe this project will achieve and by when.

Example: "This project will generate $10K MRR within 6 months by selling <product> to <ICP>."

## Validation signal (positive)

The specific, measurable, time-bound outcome that proves this project is working.

- Metric: <what you are measuring>
- Target: <specific number>
- Deadline: <specific date>

Example: "3 paid customers by 2026-07-15. Payment = bank transfer received, not verbal commitment."

## Anti-signal (kill trigger)

The specific, measurable, time-bound outcome that proves this is NOT working and warrants killing the project.

- Metric: <what you are measuring>
- Threshold: <specific number>
- Deadline: <specific date>
- Action if triggered: KILL. Shut down, redirect runway, move on.

Example: "Fewer than 1 paid customer by 2026-06-15. Trigger = pull the plug within 7 days."

## Review dates

Explicit calendar dates. Not "monthly," not "when I feel like it."

- Week 4: 2026-05-15 — checkpoint: <what you need to see by then>
- Week 8: 2026-06-15 — checkpoint: <what you need to see by then>
- Week 12: 2026-07-15 — FINAL validation or kill

## Accountability

Who holds you to this besides yourself. Must be a named person or a standing meeting.

- Primary: <name> — cadence: <weekly / biweekly / at each review date>
- Secondary (optional): <name or group>

## Signed

Date written: <YYYY-MM-DD>
Date last reviewed: <YYYY-MM-DD>

---

## Notes log

Append review notes here at each check-in. Include date, what you saw, verdict (continue / adjust / kill).
```

## What makes a good kill-criteria file

- **Numbers, not adjectives.** "3 paid customers" is good. "Good traction" is not.
- **Dates, not durations.** "By 2026-07-15" is good. "Within 3 months" is acceptable only if accompanied by the computed date.
- **Definitions.** "Paid customer" should be defined (bank transfer received? signed contract? verbal commitment?). Ambiguity here destroys the trigger.
- **Anti-signal that will actually trigger.** Many founders write anti-signals so lenient they'll never fire. The anti-signal should force a real choice at the deadline.
- **Accountability that is not self.** A named person, a standing meeting, or a weekly review call. If you only answer to yourself, assume the criteria won't be enforced.

## What to do when a review date arrives

On a review date, append to the Notes log:

- Date
- What you observed (actual metrics vs. target)
- Verdict: continue, adjust, or kill
- If adjust: what changes to the criteria (and why)
- If kill: commit to the shutdown date (ideally within 7 days)

If the verdict is "adjust," question whether you are moving the goalposts to avoid a kill. That is the failure mode this file exists to prevent.
