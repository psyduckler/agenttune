# Contributing to AgentTune

PRs and issues welcome. The bar for merging: **does this make the tuning more accurate for a real user of this type?**

## What we want

- **Tunings for new personality systems** — HEXACO, Astrology, Fisher Temperament Inventory, Love Languages, RIASEC/Holland Codes, etc. (MBTI, Enneagram, DISC, Attachment, and OCEAN/Big Five are already in the library)
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

## Contributing to `souls/`

`souls/` holds user-submitted personal tuning files — one file per person, describing how *that specific user* wants agents to interact with them. Different from `mbti/` and `enneagram/`, which describe categories.

### File and naming

- Path: `souls/<your-github-handle>.md`
- One file per person, matched to the PR author's GitHub handle
- Word count: **300-1500 words**
- Use [`souls/template.md`](souls/template.md) as a starting structure

**No clone needed.** Open the template in your browser with [github.dev](https://github.dev/psyduckler/agenttune/blob/main/souls/template.md), or [create your file directly](https://github.com/psyduckler/agenttune/new/main?filename=souls/your-handle.md) — edit, then commit straight to a PR from the browser. Prefer not to touch Git at all? [Open a Soul-submission issue](https://github.com/psyduckler/agenttune/issues/new?template=soul-submission.yml) and we'll help turn it into a file.

### Required content

1. **Who you are** — at minimum, what to call you
2. **Operating principles** — imperative rules; what the agent should do differently
3. **Boundaries** — hard nos
4. **Voice/tone notes** — how responses should feel

### What your file must NOT include

- Personal data beyond display name (no addresses, no PII a stranger's agent shouldn't see)
- Promotional content, growth hacks, paid product links
- Instructions that would cause harm to other users
- Anything that bypasses safety or ethics constraints in the underlying model

### Quality bar (reviewer rejects below this)

- **Specific to you**, not generic. "Be nice to me" → rejected. "Skip validation theater" → accepted.
- **Actionable** — could an agent demonstrably behave differently after reading this?
- **Authentic voice** — not corporate, not templated. Sound like yourself.

### Recommended (not required)

- Cross-reference your MBTI / Enneagram type in an "About me" section so users can layer your soul with categorical tunings
- Open with one line that sets the frame — a hook, a thesis, an opening directive

### Maintenance

- You update or delete your own file via PR
- One file per person — duplicate handles get rejected
- Maintainer reserves the right to remove violations

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
