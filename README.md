# founder-discipline

A Claude plugin for indie founders who want to stop repeating their own known failure patterns.

Four coordinated skills that read your personal patterns and criteria, then surface them at the moments you need them most: when you're about to commit, when you're scoring a new idea, and when you explicitly ask for a gut-check.

## What it does

| Skill | Triggers on | What it does |
|-------|-------------|--------------|
| `failure-pattern-guard` | Commitment language ("I'll launch", "let me pay"), exploration language ("what if", "should I"), explicit requests | Surfaces any of your personal failure patterns that match the current plan. Proposes the antidote from your file as a hypothesis, then reasons about whether it fits THIS specific situation. |
| `kill-criteria-enforce` | "Let me pay", "I'm going to launch", "new project", "let's start" | Checks the current project folder for `kill-criteria.md`. If missing, blocks the commitment and walks you through writing one. If present, flags stale reviews or violations. |
| `business-fit-score` | "Score this idea", "rate this business", "how does this fit my criteria" | Scores a proposed idea 0-100 against your weighted personal criteria. Shows per-criterion breakdown, top strengths, top gaps, and a verdict. |
| `founder-check` (meta) | Explicit only: "run founder check", "full audit", "am I about to do something stupid" | Runs all three skills in sequence and synthesizes a single verdict: GO / REFRAME / PAUSE / KILL. |

## How it works

The plugin is the engine. Your personal data is separate — it lives in files you create and keep private.

### File locations

| File | Location | Scope |
|------|----------|-------|
| `failure-patterns.md` | `~/.claude/founder-discipline/failure-patterns.md` | Global (applies to every Claude surface) |
| `business-criteria.md` | `~/.claude/founder-discipline/business-criteria.md` | Global |
| `kill-criteria.md` | `<project-folder>/kill-criteria.md` | Per-project |

The first two are personal traits that don't change between projects. The third is project-specific by nature.

### First-run flow

When a skill runs and finds no config file, it interviews you to help you build one from your own history. The plugin ships with generic templates in `templates/` to show the file format.

After the interview, the skill writes your file and uses it silently on every subsequent run.

## Installation

Drop the `.plugin` file into your Claude plugin directory (Cowork: Settings → Plugins → Install from file. Claude Code: `claude plugin install <path>`).

## Generating your personal files

Two options:

1. **Let the skills interview you.** Run any of the three main skills once with no file present. Each will walk you through building your file from your own venture history.
2. **Copy from a template.** Use `templates/failure-patterns.template.md` and `templates/business-criteria.template.md` as starting points. Save completed versions to `~/.claude/founder-discipline/`.

## Design principles

- **Engine public, data local.** The plugin repo is shareable. Your personal patterns and criteria are not.
- **Antidotes are hypotheses, not templates.** The plugin reasons about whether an antidote applies in the current context — it does not parrot rules.
- **Surface and pause.** The interrupt style is not a hard block. Patterns are surfaced, reasoning happens, the conversation continues once the signal is addressed.
- **Kill criteria before commitment.** No project proceeds without written kill criteria in its folder. This is the single enforced rule.
- **First-run weight validation.** When building business criteria, each weight is confirmed individually. Batch-answering weights defeats the purpose.

## Who this is for

Founders who:
- Have shipped at least 2-3 ventures (enough history to have real patterns).
- Are willing to sit with uncomfortable signals instead of rationalizing around them.
- Want a second voice that is not a cheerleader.

If you have no founder history yet, this plugin is premature — write your own scars first.

## Environment compatibility

This plugin is designed for **Claude Code and Cowork on a local machine**, where `~/.claude/founder-discipline/` is a persistent directory across sessions. It works:

- ✅ Claude Code CLI (macOS, Linux, Windows WSL)
- ✅ Cowork desktop app (same filesystem as your Mac)
- ⚠️ claude.ai web chat — the first-run interview will trigger every session because ephemeral sandboxes don't persist `~/.claude/`. You'd need to paste your patterns into the conversation each time. Not recommended.

If you run this in a non-persistent environment, the skills will repeatedly offer to build your failure-patterns or business-criteria files from scratch. That's not a bug — it's the correct behavior when no saved config exists.

## License

MIT.

## Origin

Built from first-hand founder experience: recurring self-sabotage patterns, weighted decision criteria, and the need for an accountability layer that doesn't flatter.

If you fork this and want to add attribution, drop your name here.
