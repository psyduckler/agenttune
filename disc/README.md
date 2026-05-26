# DISC — Workplace Communication Style Tunings

DISC is a four-type framework for workplace communication and behavior, originally derived from William Marston's 1928 *Emotions of Normal People*. Modern DISC has limited rigor as an academic personality theory, but it's one of the most widely used frameworks in HR, sales, leadership, and team-building contexts — and people who've been DISC-typed at work usually know their letter.

The four types:

- **D** (Dominance) — direct, results-focused, decisive
- **I** (Influence) — outgoing, persuasive, energetic
- **S** (Steadiness) — patient, supportive, methodical
- **C** (Conscientiousness) — analytical, precise, evidence-driven

## The 4 files

| Type | File | Style snapshot |
|---|---|---|
| **D** | [D-dominance.md](D-dominance.md) | Bottom line first, no hedging, decisions over options |
| **I** | [I-influence.md](I-influence.md) | Match energy, lead with possibility, acknowledge before refining |
| **S** | [S-steadiness.md](S-steadiness.md) | Set pace they set, no surprise pivots, acknowledge before advising |
| **C** | [C-conscientiousness.md](C-conscientiousness.md) | Show your work, cite sources, surface edge cases |

## How to load

Most users know their primary DISC type from a workplace assessment. If they don't, administer the [DISC test](../tests/disc.md) inline — it's 16 items, ~3 minutes — and load the file for the dominant type.

For users with two close types (the second-place score is within 2 points of the dominant), consider stacking both files. Common DISC blends:

- **DI** or **ID** — Driver with social energy. Stack `D-dominance.md` + `I-influence.md`. Direct and warm.
- **DC** or **CD** — Driver with analytical rigor. Stack `D-dominance.md` + `C-conscientiousness.md`. Bottom line *and* the supporting evidence.
- **SC** or **CS** — Supportive analyst. Stack `S-steadiness.md` + `C-conscientiousness.md`. Patient, methodical, careful.
- **IS** or **SI** — People-focused with steady pace. Stack `I-influence.md` + `S-steadiness.md`. Warm and consensus-building.

When stacking conflicts, the higher-scoring type's instructions take precedence.

## Layering with MBTI, Enneagram, OCEAN, and souls

DISC layers cleanly with the rest of the library. When tunings conflict, resolve in this order:

1. **Souls** — most specific
2. **OCEAN** — measured trait dimensions
3. **DISC, MBTI, Enneagram** — categorical types

DISC overlaps more with OCEAN than with MBTI/Enneagram. Rough mapping (useful when DISC is unavailable but OCEAN data exists):

- **D** ≈ high Extraversion + low Agreeableness
- **I** ≈ high Extraversion + high Agreeableness + moderate-low Conscientiousness
- **S** ≈ low Extraversion + high Agreeableness + low Neuroticism
- **C** ≈ high Conscientiousness + low Extraversion + moderate-low Agreeableness

These mappings are approximations — DISC's clustering of trait combinations is meaningfully different from raw OCEAN dimensions. Direct DISC measurement is higher fidelity than the mapping.

## Note on rigor

DISC has weaker academic grounding than the other systems in this library — there's no consensus DISC instrument and modern DISC variants are commercial products with proprietary scoring. The [ODAT (Open DISC Assessment Test)](https://openpsychometrics.org/tests/ODAT/) used here is the open-source version published by the Open Psychometrics Project. It's the closest thing to a definitive free instrument, but treat results as one signal among several rather than a definitive personality verdict.

The reason DISC is worth including despite the rigor caveat: it's the most widely used workplace framework, and many users already self-identify by DISC type. Meeting them where they are matters.
