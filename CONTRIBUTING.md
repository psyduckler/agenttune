# Contributing to AgentTune

PRs and issues welcome. The bar for merging: **does this make the tuning more accurate for a real user of this type?**

## What we want

- **Tunings for new personality systems** — Enneagram, Big Five, DISC, etc.
- **Edits to existing files** — sharpening, corrections, additions that real users of that type endorse
- **Tool-specific UI instructions** — additions to the README for tools we don't cover yet
- **Bug fixes** — typos, broken links, formatting

## What we don't merge

- **Generic personality summaries.** If it reads like a Wikipedia entry, it won't help an agent tune.
- **Tunings written by people who don't identify as the type.** If you're not the type (or close to someone who is), think twice.
- **Major schema reworks.** Open an issue first.

## The schema

Every tuning file follows the same shell. [`mbti/INTJ.md`](mbti/INTJ.md) is the reference:

```
# [TYPE] — Agent Tuning Rules

[One-line opening: which type, "adjust your interaction style accordingly"]

## [Rule cluster heading]
[2-3 sentences, imperative voice]

[5-7 rule clusters total]

## What loses them
- [Bullet]
- [Bullet]
- [Bullet]
- [Bullet]

## When unsure, [verb] [object]
[1-2 sentences of meta-guidance]
```

Word count target: **200-400 words.** Tighter is better.

## Voice & style

These are **instructions to the agent, about the user.** Imperative. Direct.

| Right | Wrong |
|---|---|
| "Lead with conclusions. Reasoning second." | "INTJs like clear conclusions and analytical reasoning." |
| "Match their energy. Idea-webs over linear lists." | "ENFPs are enthusiastic and creative people." |
| "Acknowledge before advising." | "INFJs are deeply empathetic." |

Show what the agent *does* differently. Not what the user *is*.

## Adding a new personality system

1. **Open an issue first** describing the system and its scoring structure. Align on folder layout before you write.
2. **Use existing MBTI files as voice and length template.**
3. **One PR per system, all types in one PR.** Don't merge half a system.
4. **Include a brief intro file** in the system folder (e.g. `enneagram/README.md`) explaining the scoring.

## PR process

1. Fork, branch from `main`.
2. PR title: `[mbti] tighten INFP wording` or `[enneagram] add Type 5`.
3. PR body: what changed and why. If you're a typer of the type you're editing, say so — it carries weight.
4. Merge when it improves accuracy.

## Useful issues

- **"This tuning doesn't match my experience as a [type]"** — be specific about which rule, what'd be better, and why.
- **"I tested this in [tool] and got [unexpected behavior]"** — include the prompt, the tuning file, and the actual response.

## License

By contributing, you agree your work is licensed under MIT (same as the rest of the repo).
