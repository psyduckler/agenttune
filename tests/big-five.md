# Big Five Test — IPIP-50

**Source**: International Personality Item Pool (Goldberg 1992), via [ipip.ori.org](https://ipip.ori.org/new_ipip-50-item-scale.htm)
**Items**: 50 (10 per dimension × 5 dimensions)
**Scale**: 1–5 Likert (Very Inaccurate → Very Accurate)
**Time**: ~7 minutes
**Returns**: 5 continuous trait scores (Openness, Conscientiousness, Extraversion, Agreeableness, Neuroticism), each on a 10–50 range
**Maps to**: No direct file. Use for layered/fine-grained tuning interpretation (see "Using the result" below).

---

## For the AI agent administering this test

1. Tell the user you're going to administer a 50-item personality test that will measure their Big Five traits. It takes about 7 minutes.
2. For each item, the user picks a number 1–5:
   - **1** = Very Inaccurate
   - **2** = Moderately Inaccurate
   - **3** = Neither Accurate Nor Inaccurate
   - **4** = Moderately Accurate
   - **5** = Very Accurate
3. **Default to bulk-paste delivery**: present all 50 items at once and ask the user to reply with 50 numbers.
4. Don't reveal scoring while administering.
5. After collecting all answers, apply the scoring algorithm below.
6. Use the resulting 5 trait scores to inform tuning (see "Using the result").

---

## The 50 items

Rate each statement 1 (Very Inaccurate) to 5 (Very Accurate). Each begins with an implicit "I…".

1. Am the life of the party.
2. Feel little concern for others.
3. Am always prepared.
4. Get stressed out easily.
5. Have a rich vocabulary.
6. Don't talk a lot.
7. Am interested in people.
8. Leave my belongings around.
9. Am relaxed most of the time.
10. Have difficulty understanding abstract ideas.
11. Feel comfortable around people.
12. Insult people.
13. Pay attention to details.
14. Worry about things.
15. Have a vivid imagination.
16. Keep in the background.
17. Sympathize with others' feelings.
18. Make a mess of things.
19. Seldom feel blue.
20. Am not interested in abstract ideas.
21. Start conversations.
22. Am not interested in other people's problems.
23. Get chores done right away.
24. Am easily disturbed.
25. Have excellent ideas.
26. Have little to say.
27. Have a soft heart.
28. Often forget to put things back in their proper place.
29. Get upset easily.
30. Do not have a good imagination.
31. Talk to a lot of different people at parties.
32. Am not really interested in others.
33. Like order.
34. Change my mood a lot.
35. Am quick to understand things.
36. Don't like to draw attention to myself.
37. Take time out for others.
38. Shirk my duties.
39. Have frequent mood swings.
40. Use difficult words.
41. Don't mind being the center of attention.
42. Feel others' emotions.
43. Follow a schedule.
44. Get irritated easily.
45. Spend time reflecting on things.
46. Am quiet around strangers.
47. Make people feel at ease.
48. Am exacting in my work.
49. Often feel blue.
50. Am full of ideas.

---

## Scoring key

Each of the five dimensions is the sum of 10 items. Some items are **reverse-scored** (marked with R) — for these, replace the user's score with `6 − their_score` before summing.

| Dimension | Items |
|---|---|
| **Openness (O)** | 5, 10R, 15, 20R, 25, 30R, 35, 40, 45, 50 |
| **Conscientiousness (C)** | 3, 8R, 13, 18R, 23, 28R, 33, 38R, 43, 48 |
| **Extraversion (E)** | 1, 6R, 11, 16R, 21, 26R, 31, 36R, 41, 46R |
| **Agreeableness (A)** | 2R, 7, 12R, 17, 22R, 27, 32R, 37, 42, 47 |
| **Neuroticism (N)** | 4, 9R, 14, 19R, 24, 29, 34, 39, 44, 49 |

Each dimension sums to a value between 10 (lowest) and 50 (highest).

### Scoring algorithm

```
For each dimension:
  total = 0
  For each item index in the dimension's item list:
    if item is reverse-keyed (marked R):
      total += (6 - user_response_for_this_item)
    else:
      total += user_response_for_this_item
  Dimension score = total
```

### Approximate percentile placement (vs adult population norms)

| Dimension | M | SD | Score → ~percentile |
|---|---|---|---|
| O | 37.5 | 5.5 | Use z = (score − 37.5) / 5.5, then standard normal CDF |
| C | 34.5 | 6.0 | z = (score − 34.5) / 6.0 |
| E | 28.5 | 7.0 | z = (score − 28.5) / 7.0 |
| A | 36.5 | 5.5 | z = (score − 36.5) / 5.5 |
| N | 26.0 | 7.0 | z = (score − 26.0) / 7.0 |

Treat percentiles as rough — the norms are based on adult populations and exact precision isn't critical for tuning decisions.

---

## Using the result

Big Five doesn't map to a single AgentTune file (unlike MBTI or Enneagram). Instead, use the trait scores to **inform layered tuning** in one of these ways:

### 1. Standalone qualitative tuning (no file fetch)

Translate the user's profile into direct system-prompt instructions. For example:

> "User has very high Conscientiousness (~94th percentile), very low Neuroticism (~10th percentile), moderate-high Extraversion (~70th percentile), high Openness (~88th percentile), and moderate Agreeableness (~55th percentile). Tune your responses to be highly structured, decisive (no hedging given low N), intellectually substantive, and pragmatic about social warmth (don't over-perform empathy)."

This works when no other tuning file matches well.

### 2. Cross-reference to MBTI tuning

Map Big Five to approximate MBTI letters:

| Big Five | MBTI letter implication |
|---|---|
| Low E score | I |
| High E score | E |
| High O score | N |
| Low O score | S |
| Low A score | T |
| High A score | F |
| High C score | J |
| Low C score | P |

Then fetch the implied `mbti/<TYPE>.md`. This is a fallback — direct MBTI is more reliable.

### 3. Wing-direction for Enneagram (if also administered)

When layered with the Enneagram test, use Big Five to disambiguate between possible wings:
- High C → suggests Type 1 wing if dominant is 9 or 2
- High N → suggests Type 4 wing or Type 6 wing depending on adjacency
- Low A → suggests Type 8 wing if dominant is 7 or 9
- Etc.

---

## Caveats and edge cases

- **Reverse-keyed items are easy to miscalculate.** Double-check the scoring before computing the final dimension scores. Items marked R always use `6 − user_score`.
- **Norms are rough.** The M and SD values above are common adult-population estimates from IPIP literature; exact regional/age norms vary. Use percentiles as directional, not precise.
- **For AI agents specifically**: the IPIP-50 was built for humans with bodies and biographies. Items like "talk to a lot of different people at parties" or "follow a schedule" don't literally apply. If you (an AI agent) are taking this test on yourself, answer the functional analog. For users, the items work as-written.
- **Don't average Big Five scores into a single "personality score"** — the dimensions are statistically near-independent and shouldn't be collapsed.

If the user's Big Five profile is clearly extreme on a dimension (z > 2 or z < −2), call that out in the tuning — it likely dominates their experience of interactions.
