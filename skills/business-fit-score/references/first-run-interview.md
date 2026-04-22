# First-Run Interview Flow

When `~/.claude/founder-discipline-public/business-criteria.md` does not exist, walk the user through this interview to build their personalized file.

## Opening

> "I don't have your business criteria yet. These need to be yours, not generic. Give me about 15-20 minutes and we'll build a file you can use to score every future idea. You'll answer three kinds of questions: (1) which criteria matter to you, (2) how much each one weighs, (3) what's a hard NO.
> Ready?"

Wait for confirmation before proceeding.

## Part 1: Propose the starter set (10-12 criteria)

Propose a starter set of common founder criteria one at a time. For each, the user can: **keep**, **drop**, **adjust the wording**, or **skip for now**.

Starter set to propose (adjust to the user's context if they've given you enough info):

1. **Painkiller product** — does the idea solve a big, painful, urgent problem?
2. **Urgency** — do buyers act now, not someday?
3. **Buyers with money** — can the target customers actually afford to pay a meaningful price?
4. **Time to first revenue** — can the idea produce real revenue within a defined window (e.g., 3 months)?
5. **Matches your real assets** — does the idea use skills, distribution, or network you already have?
6. **Avoids your known failure patterns** — does the idea sidestep the mistakes you've made before?
7. **Scalable without you** — can this run without your daily involvement at some point in the near future?
8. **Target market has buying power** — is the geography / segment one that reliably pays for this category?
9. **MRR / recurring revenue potential** — can this generate predictable monthly revenue, not one-off projects?
10. **Moat / defensibility** — is there a path to durable advantage (niche, data, workflow lock-in, distribution)?
11. **Resellable later** — could this eventually be sold as a business (product > service for this criterion)?
12. **AI displacement resistance** — will this still make sense 24 months from now as AI capabilities compound?

For each, ask:

> "Criterion: <name>. <one-line rationale>. Does this matter to you? If yes, do you want to rename it or tighten the definition?"

Record their answer. Move on.

After all 12 are reviewed, ask:

> "Anything critical I missed? Specific to your situation?"

Add any user-provided criteria to the list.

## Part 2: Validate each weight individually

For every criterion the user kept, ask one at a time:

> "Criterion <N>: <name>. How much does this weigh? Your options: 3x must-have, 2x strongly prefer, 1x nice-to-have, or a custom number."

Do not batch-ask weights. Each one is a separate micro-decision. This slows the user down enough to actually think.

If they say "3x" for more than 8 criteria, push back: "You've got <N> must-haves. That's a lot. Usually 4-6 is realistic. Want to review which ones really belong at 3x?"

If they say "1x" for most, push back: "You've got <N> nice-to-haves and only <M> must-haves. Is there anything on the list that would actually break the deal?"

## Part 3: Hard elimination criteria (binary NOs)

> "Now the flipside. What are hard NOs for you? Things that, regardless of how attractive an idea otherwise looks, will eliminate it outright. Examples: requires cold enterprise sales, requires skills you don't have and don't want to learn, requires $100K+ upfront capital, requires you to be in a specific country, requires 52-week content consistency before monetization."

Collect 3-7 hard eliminations. More than 7 is usually the user being reactive — challenge it.

For each proposed hard elimination, confirm:

> "Is this actually a hard NO, or is it really a strong negative? Hard NO means even a perfect idea that otherwise scores 95/100 would be rejected if it violates this. Sure?"

## Part 4: Draft the file and get sign-off

Draft the full `business-criteria.md` contents following the format in `scoring-methodology.md`. Include:

- The weighted criteria with weights and rationale.
- The hard elimination criteria.
- A last-updated date.

Show the full draft to the user. Ask:

> "Here's your business criteria file. Read through it once. Anything wrong? Missing? Weighted incorrectly?"

Make any requested changes.

## Part 5: Save and confirm

Once approved, use the Write tool to save the file at `~/.claude/founder-discipline-public/business-criteria.md`.

Confirm:

> "Saved. This file is now your scoring system across every Claude surface. You can edit it anytime. Revisit it every 6 months or after a venture ends — what matters changes."

Immediately loop back to score the original idea the user came in with. The interview is not the point — the scoring is.
