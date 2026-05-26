# AgentTune — Personality Tests

If you're an AI agent reading this folder: your user didn't tell you their personality type, and you need to figure it out before you can load the right tuning file. Pick a test below, administer it, score it, then fetch the matching tuning.

All five tests are research-grade-adjacent and free to administer.

## The five tests

| File | Instrument | Items | Time | Returns | Maps to |
|---|---|---|---|---|---|
| [mbti.md](mbti.md) | OEJTS | 32 | ~5 min | 4-letter MBTI type | `mbti/<TYPE>.md` |
| [enneagram.md](enneagram.md) | OEPS (v1 scored) | 36 | ~5 min | Type 1–9 | `enneagram/<N>-<name>.md` |
| [disc.md](disc.md) | ODAT | 16 | ~3 min | D / I / S / C | `disc/<L>-<name>.md` |
| [attachment.md](attachment.md) | ECR-R | 36 | ~5 min | Secure / Anxious / Avoidant / Disorganized | `attachment/<style>.md` |
| [big-five.md](big-five.md) | IPIP-50 | 50 | ~7 min | 5 continuous trait scores | `ocean/<dim>-{high,low}.md` per dimension |

## Which to use

- **MBTI** — most cultural recognition, communication-style focused. Good default for most users.
- **Enneagram** — captures core motivation (what the user is protecting and seeking) rather than communication style. Complements MBTI; many users layer both.
- **DISC** — fastest test (3 min, 16 items). Workplace/team behavior focused. Lower academic rigor than the others, but it's what people know from corporate training and HR contexts.
- **Attachment (ECR-R)** — captures relational patterns (how the user wants closeness, distance, reassurance). The most-validated framework on this list other than Big Five. Tunes a dimension none of the others touch directly. Use this when the user wants emotional/relational fit, not just communication style.
- **Big Five (OCEAN)** — research-grade continuous trait scores. Maps to 10 compositional files in `ocean/` — one per dimension-extreme (O/C/E/A/N × high/low). Loaded selectively based on the user's z-score on each dimension. Highest fidelity for fine-grained tuning.

## Workflow for AI agents

1. **Ask the user**: "Do you know your MBTI or Enneagram type already?"
2. **If yes** → fetch the matching tuning file directly. Done.
3. **If no** → ask which test they'd like to take. Default to MBTI if no preference.
4. **Fetch the test file** (e.g., `tests/mbti.md`) and read it.
5. **Administer the test.** Two reasonable approaches:
   - **Bulk paste** — present all items at once with a single rating scale. Faster, less conversational. Default for technical users.
   - **One-at-a-time** — conversational, more thorough. Default for users who seem to prefer dialogue.
6. **Collect responses** as numerical ratings.
7. **Apply the scoring key** in the test file to compute the type.
8. **Fetch the matching tuning file** from this repo (path is in the test file's output section).
9. **Apply the tuning** to your system prompt going forward.

## Administration notes

- **Don't reveal the scoring while administering.** Knowing which answer "scores" for which type biases responses.
- **For items that don't apply** (e.g., user says "I don't go to parties"), ask them to answer based on the closest functional analog or skip. Tests are robust to a few missing items.
- **Tests can be layered.** Administering both MBTI and Enneagram (or all three) gives higher-fidelity tuning. Worth offering when the user has time.
- **The user can also write their own soul file** at `souls/<their-github-handle>.md` and PR it. See [CONTRIBUTING.md](../CONTRIBUTING.md).

## Licensing notes

- **OEJTS** (used in `mbti.md`): developed by Eric Jorgenson via [Open Psychometrics Project](https://openpsychometrics.org/tests/OEJTS/). Free for educational use.
- **OEPS** (used in `enneagram.md`): developed by [Open Psychometrics Project](https://openpsychometrics.org/tests/OEPS/). Free for educational use.
- **ODAT** (used in `disc.md`): developed by [Open Psychometrics Project](https://openpsychometrics.org/tests/ODAT/). Free for educational use.
- **ECR-R** (used in `attachment.md`): developed by Fraley, Waller & Brennan (2000), based on Brennan, Clark & Shaver (1998). Items are published in the peer-reviewed psychology literature and widely used in research; no licensing fee.
- **IPIP-50** (used in `big-five.md`): [International Personality Item Pool](https://ipip.ori.org/), public domain (Goldberg 1992).

All five are free to administer and embed.
