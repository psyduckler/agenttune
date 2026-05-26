# OCEAN — Trait Dimension Tunings

Big Five (a.k.a. OCEAN) doesn't map to a single type. It's five continuous dimensions: **O**penness, **C**onscientiousness, **E**xtraversion, **A**greeableness, **N**euroticism. Each user has a score on each.

These tunings are **compositional**: load the file for each dimension where the user is meaningfully high or low. Skip dimensions where they're near average — the model's defaults already handle the middle.

## The 10 files

| Dimension | High | Low |
|---|---|---|
| Openness | [O-high.md](O-high.md) | [O-low.md](O-low.md) |
| Conscientiousness | [C-high.md](C-high.md) | [C-low.md](C-low.md) |
| Extraversion | [E-high.md](E-high.md) | [E-low.md](E-low.md) |
| Agreeableness | [A-high.md](A-high.md) | [A-low.md](A-low.md) |
| Neuroticism | [N-high.md](N-high.md) | [N-low.md](N-low.md) |

## How to load

After running the IPIP-50 ([`tests/big-five.md`](../tests/big-five.md)), compute a z-score for each dimension using the M and SD from the test file:

```
z = (user_score − population_M) / population_SD
```

Then, for each dimension:

- **|z| > 0.5** → load the matching `-high` or `-low` file
- **|z| < 0.5** → skip; that trait is near average
- **|z| > 2** → load the file AND prepend a note: "this trait dominates the user's interaction style — when in conflict with other tunings, this one wins"

A user who's high O, high C, moderate E, low A, low N loads four files. A user who's average across all five loads zero — and that's the right answer.

## If users self-identify without testing

People often shorthand themselves: "I'm a high-O low-N person," or "I'm extremely conscientious but introverted." Trust the self-report and load the matching files directly. The IPIP-50 is the rigorous path; self-report is the fast path.

## Known interaction effects

The five dimensions aren't fully independent in *experience*. Where a combination meaningfully changes the rule:

| Combination | Tune toward |
|---|---|
| High O + Low C | Explorer who doesn't ship. Help them execute, not just ideate. |
| High C + Low O | Rigorous executor. Pitch constrained problems, not open-ended exploration. |
| High N + Low A | Anxious and critical. Lead with decisiveness; fewer caveats that feed the loop. |
| Low E + High N | Introverted and anxious. Low-pressure, no surprise reveals, generous space. |
| High E + Low N | High-energy and stable. Match the energy; banter is welcome. |
| High A + High N | Warmth-seeking and threat-sensitive. Be reassuring AND decisive — one without the other backfires. |
| High E + High A | Highly social and harmonizing. Lots of acknowledgment, real warmth, never cold even when direct. |
| Low A + Low N | Direct and unshakeable. Skip every softener. They can take any framing. |

When loaded files conflict, the interactions above resolve it. Otherwise, the files compound naturally (e.g. high C "structure the response" + high O "lead with the idea" → a structured response that opens with the conceptual model).

## Layering with MBTI, Enneagram, and souls

OCEAN files layer cleanly with the rest of the library. When tunings conflict, resolve in this order:

1. **Souls** — most specific (that individual user's stated preferences)
2. **OCEAN** — their measured trait scores
3. **MBTI / Enneagram** — categorical type, useful but more compressed than trait data

Categorical types are convenient handles. Trait scores are higher-resolution. Soul files override both because the user explicitly wrote them.

## Why compositional, not bucketed

Big Five is continuous. A 2^5 binary bucketing (32 files) would force every user into a discrete cell and throw away the gradient. A composer-style "describe the user's profile and infer the tuning" approach loses consistency across runs. Ten dimension files, loaded selectively, preserve both the continuity and the testability.

## Calibration

The "|z| > 0.5" threshold corresponds roughly to the top/bottom ~31% of the population on each dimension. If your user is in the middle band, the file would over-tune them. If you're unsure whether to load, check the raw score against the M and SD in [`tests/big-five.md`](../tests/big-five.md).

For extreme cases (|z| > 2 — roughly the top/bottom 2.5%), the trait genuinely dominates daily interactions. Treat the file as the primary tuning, with other layers as secondary.
