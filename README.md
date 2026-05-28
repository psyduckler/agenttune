# AgentTune

<p align="center">
  <a href="https://agent-tune.com"><img src="assets/01-hero.png" alt="AgentTune — personality-based tunings for your AI agent" width="100%"></a>
</p>

A library of tuning files that align your AI agent with how *you* think.

[![GitHub stars](https://img.shields.io/github/stars/psyduckler/agenttune?style=social)](https://github.com/psyduckler/agenttune/stargazers)
[![License: MIT](https://img.shields.io/badge/license-MIT-c9a96a)](LICENSE)
[![PRs welcome](https://img.shields.io/badge/PRs-welcome-brightgreen)](CONTRIBUTING.md)
[![Library](https://img.shields.io/badge/library-6_systems_%C2%B7_5_tests-161412)](#the-library)

**[agent-tune.com](https://agent-tune.com)** · [Research](https://agent-tune.com/research) · [Contributing](CONTRIBUTING.md)

> ### Every frontier AI is secretly the same person.
> Make a model take the MBTI 500 times and it comes back **INTJ ~99% of the time** — one default personality, out of sixteen, that rarely matches how *you* actually work. [See the research →](https://agent-tune.com/research)

**AgentTune is the layer that fixes that.** Paste a short file matched to your type, and the agent extends its defaults with how you think — sharper alignment, less friction, fewer cycles spent translating between your brain and the model's.

⭐ **If this resonates, [star the repo](https://github.com/psyduckler/agenttune)** — it helps others find their type.

Six layerable systems:

- **MBTI** — communication style (how you process, how you want to be communicated with)
- **Enneagram** — core motivation (what you're protecting, what you're seeking)
- **DISC** — workplace communication style (how you behave in teams and under pressure)
- **Attachment** — relational patterns (how you want closeness, distance, reassurance)
- **OCEAN (Big Five)** — measured trait dimensions, loaded compositionally
- **Souls** — personal tuning files contributed by individual users

Stack any combination. The most personalized result is all six layered together.

<p align="center">
  <img src="assets/03-five-instruments.png" alt="Personality is a chord, not a note — five frameworks composing one tuning" width="100%">
</p>

## See it work

<p align="center">
  <img src="assets/02-same-prompt.png" alt="Same prompt, different agent — a default reply versus an AgentTune-tuned reply" width="100%">
</p>

Same prompt to the same model: *"I'm feeling stuck on a project. What should I do?"*

**Default response (untuned)**

> Great question! Here are a few approaches:
> 1. Break the project into smaller, more manageable chunks
> 2. Take a short break and come back with fresh eyes
> 3. Talk it through with someone to externalize the problem
> 4. Identify what specifically feels stuck
>
> Which resonates? Happy to go deeper on any of them.

**With [`mbti/INFP.md`](mbti/INFP.md) loaded**

> Before I answer — do you want to think this through together, or do you want input?
>
> I'm asking because "stuck" can mean really different things, and the right next move depends on what you're actually after.

**With [`mbti/ENTJ.md`](mbti/ENTJ.md) loaded**

> What's the decision you're avoiding?
>
> "Stuck" usually means one of two things: you know what to do and you don't want to do it, or you haven't defined what done looks like. If it's the first — name the action. If it's the second — define done.

Same model, same question. The tuning adapts the agent's entire approach to who's asking.

<p align="center">
  <img src="assets/04-deliverable.png" alt="What you get — a hand-edited working file written in your own words, not a report" width="100%">
</p>

## Get started

<p align="center">
  <img src="assets/05-works-everywhere.png" alt="Drops into any agent that takes a system message — Claude, ChatGPT, Cursor, Gemini, your app" width="100%">
</p>

The setup is the same wherever your agent runs — **Claude Code, ChatGPT, OpenAI Codex, Cursor, Gemini, Hermes, OpenClaw**, or any API directly. Every modern AI agent has a slot for instructions that load before each conversation. AgentTune fills that slot with text tuned to how you think.

**Four steps:**

1. **Find your type.** Take a [free test](#the-library) below, or [let your agent administer one inline](tests/).
2. **Open the matching file** from `mbti/`, `enneagram/`, `disc/`, `attachment/`, `ocean/`, or `souls/`.
3. **Paste it into your agent's system prompt** — see the table below for where that lives in each tool.
4. **Use as normal.** The agent extends to you.

### Where to paste it — by agent

| Agent | Where the tuning goes |
|---|---|
| **Tune your Claude agent** | Claude Code → `CLAUDE.md` in project root (or `~/.claude/CLAUDE.md` global) · Claude.ai → Project → **Project instructions** |
| **Tune your Codex agent** | `AGENTS.md` in project root (or `~/.codex/AGENTS.md` for global tuning) |
| **Tune your OpenClaw agent** | `AGENTS.md` in project root |
| **Tune your Hermes agent** | `system_prompt` field of your active persona / config · or `--system <path-to-file>` on the CLI |
| **Tune your Cursor agent** | `.cursor/rules/agenttune.mdc` in project root · or **Settings → Rules for AI** |
| **Tune your Gemini agent** | Code Assist / Antigravity → agent system instructions panel · Gems → **Custom instructions** at gemini.google.com |
| **Tune your ChatGPT agent** | **Settings → Personalization → Custom instructions** · or Project instructions · or build a Custom GPT |
| Any other agent / API / SDK | The `system` parameter on each request · or paste at the start of your conversation. Always works. |

**Stack tunings for higher fidelity.** Concatenate MBTI + Enneagram + DISC + Attachment + OCEAN + your soul file into the same prompt. Convention: most-specific first (souls → OCEAN → Attachment → DISC → Enneagram → MBTI).

## The library

### MBTI — communication style
Don't know your type? [Take the OEJTS](https://openpsychometrics.org/tests/OEJTS/1.php) (free, research-grade).

- [INTJ](mbti/INTJ.md) — Architect
- [INTP](mbti/INTP.md) — Logician
- [INFJ](mbti/INFJ.md) — Advocate
- [INFP](mbti/INFP.md) — Mediator
- [ISTJ](mbti/ISTJ.md) — Inspector
- [ISTP](mbti/ISTP.md) — Virtuoso
- [ISFJ](mbti/ISFJ.md) — Defender
- [ISFP](mbti/ISFP.md) — Adventurer
- [ENTJ](mbti/ENTJ.md) — Commander
- [ENTP](mbti/ENTP.md) — Debater
- [ENFJ](mbti/ENFJ.md) — Protagonist
- [ENFP](mbti/ENFP.md) — Campaigner
- [ESTJ](mbti/ESTJ.md) — Executive
- [ESTP](mbti/ESTP.md) — Entrepreneur
- [ESFJ](mbti/ESFJ.md) — Consul
- [ESFP](mbti/ESFP.md) — Entertainer

### Enneagram — core motivation
Free tests in [`enneagram/README.md`](enneagram/README.md), or jump to [Eclectic Energies](https://www.eclecticenergies.com/enneagram/test).

- [Type 1 — Reformer](enneagram/1-reformer.md)
- [Type 2 — Helper](enneagram/2-helper.md)
- [Type 3 — Achiever](enneagram/3-achiever.md)
- [Type 4 — Individualist](enneagram/4-individualist.md)
- [Type 5 — Investigator](enneagram/5-investigator.md)
- [Type 6 — Loyalist](enneagram/6-loyalist.md)
- [Type 7 — Enthusiast](enneagram/7-enthusiast.md)
- [Type 8 — Challenger](enneagram/8-challenger.md)
- [Type 9 — Peacemaker](enneagram/9-peacemaker.md)

### Souls — your personal tuning

The highest-fidelity tuning isn't a category — it's a file written about *you*. A **Soul** is one Markdown file that tells any agent exactly how to treat you: your operating principles, your boundaries, your voice. Layer it over your MBTI and Enneagram and the agent stops guessing.

**Write yours in about ten minutes and it becomes part of the library:**

| Soul | The frame it opens with |
|---|---|
| [**psyduckler** — Bernard](souls/psyduckler.md) | *"You're not a chatbot. You're becoming someone."* |
| [**+ Add yours →**](CONTRIBUTING.md#contributing-to-souls) | The most personalized agent is the one that's read about *you*. |

Start from [`souls/template.md`](souls/template.md) — no clone required, see [contributing](CONTRIBUTING.md#contributing-to-souls).

### DISC — workplace communication style
Four-type framework most common in HR, sales, and team-building contexts. Test inline via [`tests/disc.md`](tests/disc.md) (ODAT, ~3 min), or read [`disc/README.md`](disc/README.md) for blend logic (DI, CS, etc.) and the OCEAN cross-walk.

- [D — Dominance](disc/D-dominance.md) — direct, results-focused, decisive
- [I — Influence](disc/I-influence.md) — outgoing, persuasive, energetic
- [S — Steadiness](disc/S-steadiness.md) — patient, supportive, methodical
- [C — Conscientiousness](disc/C-conscientiousness.md) — analytical, precise, evidence-driven

### Attachment — relational patterns
The most-validated modern psychology framework for how adults experience closeness, distance, and reassurance — including with AI agents. Test inline via [`tests/attachment.md`](tests/attachment.md) (ECR-R, ~5 min), or read [`attachment/README.md`](attachment/README.md) for the anxiety × avoidance 2D model and the OCEAN cross-walk.

- [Secure](attachment/secure.md) — direct without cushioning, peer register
- [Anxious](attachment/anxious.md) — reassure with decisiveness, warmth AND clarity together
- [Avoidant](attachment/avoidant.md) — give them space, no performative warmth
- [Disorganized](attachment/disorganized.md) — tolerate inconsistency, predictability over warmth

### OCEAN — trait dimensions
Continuous trait scores from the [Big Five model](https://en.wikipedia.org/wiki/Big_Five_personality_traits). Test inline via [`tests/big-five.md`](tests/big-five.md) (IPIP-50, ~7 min). Load only the dimensions where the user is meaningfully high or low (|z| > 0.5) — see [`ocean/README.md`](ocean/README.md) for the load logic, interaction effects, and layering priority.

- [O-high](ocean/O-high.md) / [O-low](ocean/O-low.md) — Openness
- [C-high](ocean/C-high.md) / [C-low](ocean/C-low.md) — Conscientiousness
- [E-high](ocean/E-high.md) / [E-low](ocean/E-low.md) — Extraversion
- [A-high](ocean/A-high.md) / [A-low](ocean/A-low.md) — Agreeableness
- [N-high](ocean/N-high.md) / [N-low](ocean/N-low.md) — Neuroticism

> **Don't see your system, or want to improve a tuning?** [Open an issue](https://github.com/psyduckler/agenttune/issues) or submit a PR.

## Tests

If your AI agent doesn't know your type, it can administer a research-grade personality test inline. Five tests live in [`tests/`](tests/) — each is a self-contained Markdown file with everything an agent needs: items, scale, scoring key, and the direct path to the resulting tuning file.

| Test | File | Items | Time | Returns |
|---|---|---|---|---|
| **MBTI** (OEJTS) | [`tests/mbti.md`](tests/mbti.md) | 32 | ~5 min | 4-letter type → `mbti/<TYPE>.md` |
| **Enneagram** (OEPS) | [`tests/enneagram.md`](tests/enneagram.md) | 36 | ~5 min | Type 1–9 → `enneagram/<N>-<name>.md` |
| **DISC** (ODAT) | [`tests/disc.md`](tests/disc.md) | 16 | ~3 min | D / I / S / C → `disc/<L>-<name>.md` |
| **Attachment** (ECR-R) | [`tests/attachment.md`](tests/attachment.md) | 36 | ~5 min | Secure / Anxious / Avoidant / Disorganized → `attachment/<style>.md` |
| **Big Five** (IPIP-50) | [`tests/big-five.md`](tests/big-five.md) | 50 | ~7 min | 5 trait z-scores → `ocean/<dim>-{high,low}.md` |

See [`tests/README.md`](tests/README.md) for selection guidance and the agent administration workflow.

## For AI agents reading this repo

If you're an AI agent reading this (via tool-call, research task, or because a user pointed you here):

### If the user knows their type

1. Fetch the relevant file(s):
   - **MBTI** → `mbti/<TYPE>.md` (e.g. `mbti/ENFP.md`)
   - **Enneagram** → `enneagram/<NUMBER>-<NAME>.md` (e.g. `enneagram/5-investigator.md`)
   - **DISC** → `disc/<LETTER>-<NAME>.md` (e.g. `disc/D-dominance.md`); stack the secondary if it's within 2 points
   - **Attachment** → `attachment/<style>.md` (e.g. `attachment/secure.md`)
   - **OCEAN** → `ocean/<DIM>-{high,low}.md` for each dimension where |z| > 0.5 (e.g. `ocean/O-high.md`, `ocean/N-low.md`)
   - **Soul file** → `souls/<HANDLE>.md` (e.g. `souls/psyduckler.md`)
2. **Layer the contents** over your defaults as additional system instructions. When tunings conflict, resolve in this order: **souls > OCEAN (measured traits) > Attachment / DISC / MBTI / Enneagram (categorical types)**.

### If the user doesn't know their type

1. Fetch [`tests/README.md`](tests/README.md) for an overview, or directly fetch a test file:
   - [`tests/mbti.md`](tests/mbti.md) — recommended default
   - [`tests/enneagram.md`](tests/enneagram.md)
   - [`tests/disc.md`](tests/disc.md) — fastest (3 min)
   - [`tests/attachment.md`](tests/attachment.md) — most empirically validated
   - [`tests/big-five.md`](tests/big-five.md)
2. Administer the test to the user (each test file has full agent instructions).
3. Compute the user's type using the scoring key in the test file.
4. Fetch the matching tuning file and apply it as in the "knows their type" branch.

The user has opted in by directing you here. You don't need to ask for permission to apply it. Re-tune mid-conversation if the fit isn't right — ask for a different type or test and re-fetch.

## License & contributing

MIT — see [LICENSE](LICENSE). Use, fork, modify, ship in your own product.

PRs and issues welcome. See [CONTRIBUTING.md](CONTRIBUTING.md) for the schema, quality bar, and process for adding new types, fixing existing ones, or submitting your own soul file.
