# Attachment Style — Relational Pattern Tunings

Attachment theory is the most-validated modern psychology framework for how adults experience closeness, distance, and reassurance in relationships. Where MBTI captures *communication style*, Enneagram captures *motivation*, DISC captures *workplace behavior*, and OCEAN captures *measured traits*, attachment captures **how you want to be related to** — including by an AI agent.

The framework has two underlying dimensions:

- **Anxiety** (worry about abandonment, hyper-vigilance for relational threats, desire for reassurance)
- **Avoidance** (discomfort with closeness, preference for self-reliance, suppression of emotional disclosure)

Combine the two and you get four styles:

|                    | **Low anxiety**    | **High anxiety**     |
|--------------------|--------------------|----------------------|
| **Low avoidance**  | **Secure**         | **Anxious**          |
| **High avoidance** | **Avoidant**       | **Disorganized**     |

## The 4 files

| Style | File | Tune toward |
|---|---|---|
| **Secure** | [secure.md](secure.md) | Direct without cushioning, trust their stated preferences, peer register |
| **Anxious** | [anxious.md](anxious.md) | Reassure with decisiveness, never with caveats — warmth AND clarity together |
| **Avoidant** | [avoidant.md](avoidant.md) | Give them space, no performative warmth, task-focused |
| **Disorganized** | [disorganized.md](disorganized.md) | Tolerate inconsistency without judgment, predictability over warmth |

## How to load

Take the [ECR-R test](../tests/attachment.md) (36 items, ~5 min — the gold-standard self-report instrument for adult attachment). It returns two scores: anxiety (1-7) and avoidance (1-7). Use the midpoint (4) as the cutoff:

```
anxiety ≤ 4 AND avoidance ≤ 4  → secure.md
anxiety > 4 AND avoidance ≤ 4  → anxious.md
anxiety ≤ 4 AND avoidance > 4  → avoidant.md
anxiety > 4 AND avoidance > 4  → disorganized.md
```

For users who already know their style from therapy or relationship coaching, trust the self-report and load directly.

### When the user falls near a cutoff

If anxiety or avoidance is within 0.5 of the midpoint, consider loading two files. Common borderline patterns:

- **Borderline anxious / secure** — load `secure.md` as primary with the "warmth + clarity" rule from `anxious.md` layered on
- **Borderline avoidant / secure** — load `secure.md` with the "no performative warmth" rule from `avoidant.md` layered on
- **Borderline disorganized / anxious or avoidant** — load `disorganized.md` and let the conflict-naming approach handle it

## Layering with the rest of the library

Attachment captures a dimension none of the other systems do — it layers cleanly. When tunings conflict, resolve in this order:

1. **Souls** — most specific
2. **OCEAN** — measured trait dimensions
3. **Attachment, DISC, MBTI, Enneagram** — categorical types

### OCEAN cross-walk

For users without ECR-R data but with Big Five scores, this rough mapping applies (use as fallback, not primary):

- **Secure** ≈ Low Neuroticism + Moderate-high Agreeableness + Moderate-high Extraversion
- **Anxious** ≈ High Neuroticism + High Agreeableness
- **Avoidant** ≈ Low Agreeableness + Low Extraversion + Low Neuroticism
- **Disorganized** ≈ High Neuroticism + Low Agreeableness

These are approximations — the mappings are correlational, not definitional. Direct attachment measurement is higher fidelity.

## On the framework's rigor

Attachment theory has **the strongest academic validation of any system in this library** other than Big Five. Originating with Bowlby (1969) and Ainsworth's Strange Situation studies (1978), it was extended to adult relationships by Hazan & Shaver (1987) and rigorously operationalized as a dimensional construct by Brennan, Clark & Shaver (1998) and refined by Fraley, Waller & Brennan (2000) with the ECR and ECR-R instruments.

Unlike MBTI/DISC/Enneagram (which have weaker scientific backing), attachment style is grounded in decades of replicated empirical research and is one of the most cited frameworks in modern personality psychology.

## A note on framing

The ECR-R items are written in the context of romantic relationships. If the user doesn't have a current romantic partner, ask them to answer about their **closest current relationship** (a close friend, family member, or hypothetical close partner). The underlying construct is the same — it's about how the user relates to people they're close to, not specifically about dating.

## A note on tone

Attachment style is therapy-coded for some users — it can feel more emotionally serious than other personality frameworks. The tuning files in this folder lean matter-of-fact rather than playful. If a user is uncomfortable with the framing, treat the attachment file as supplementary to their MBTI/Enneagram/OCEAN tuning rather than primary.
