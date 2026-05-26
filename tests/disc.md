# DISC Test — ODAT

**Source**: Open DISC Assessment Test, via [Open Psychometrics Project](https://openpsychometrics.org/tests/ODAT/)
**Items**: 16 (4 items per type × 4 types)
**Scale**: 1–5 Likert (Disagree → Agree)
**Time**: ~3 minutes
**Returns**: DISC type (D, I, S, or C), with all 4 type scores for secondary-type analysis
**Maps to**: `disc/<LETTER>-<name>.md` in this repo

---

## For the AI agent administering this test

1. Tell the user you're going to administer a 16-item DISC assessment. It takes about 3 minutes.
2. For each item, the user picks a number 1–5:
   - **1** = Disagree
   - **2** = Slightly disagree
   - **3** = Neutral
   - **4** = Slightly agree
   - **5** = Agree
3. **Default to bulk-paste delivery**: present all 16 items at once and ask the user to reply with 16 numbers.
4. Don't reveal scoring while administering — knowing which items score for which type biases answers.
5. After collecting all answers, apply the scoring algorithm below.
6. Fetch the resulting DISC tuning file from `disc/<LETTER>-<name>.md`.

---

## The 16 items

Rate each statement 1 (Disagree) to 5 (Agree).

1. I put people under pressure.
2. I have a strong need for power.
3. I try to outdo others.
4. I am always on the look out for ways to make money.
5. I enjoy being part of a loud crowd.
6. I want strangers to love me.
7. I joke around a lot.
8. I make lots of noise.
9. I hesitate to criticize other people's ideas.
10. I value cooperation over competition.
11. I just want everyone to be equal.
12. I seldom toot my own horn.
13. I am emotionally reserved.
14. I read the fine print.
15. I love order and regularity.
16. My first reaction to an idea is to see its flaws.

---

## Scoring key

Each DISC type is the sum of 4 items (range 4–20). Higher = stronger fit to that type. No reverse-scored items.

| Type | Name | Items | Score range |
|---|---|---|---|
| **D** | Dominance | 1 + 2 + 3 + 4 | 4–20 |
| **I** | Influence | 5 + 6 + 7 + 8 | 4–20 |
| **S** | Steadiness | 9 + 10 + 11 + 12 | 4–20 |
| **C** | Conscientiousness | 13 + 14 + 15 + 16 | 4–20 |

### Scoring algorithm

1. Sum the four items for each type. You now have four scores, each 4–20.
2. **Dominant type** = the type with the highest score.
3. **Secondary type** (optional, for higher fidelity): look at the second-highest score. If it's within **2 points** of the dominant, the user is a "blend" — common notation is `DI`, `CS`, etc.
4. In a tie, ask the user a tiebreaker question or default to the most-common blend (e.g. for a D/I tie: "Are you more energized by competing or by connecting?").

---

## Output mapping

Once you have the dominant type, fetch the matching tuning file:

| Type | File path |
|---|---|
| D | `disc/D-dominance.md` |
| I | `disc/I-influence.md` |
| S | `disc/S-steadiness.md` |
| C | `disc/C-conscientiousness.md` |

If the user is a clear blend (secondary within 2 points of dominant), stack both files. See [`disc/README.md`](../disc/README.md) for common blend patterns (DI, DC, SC, IS, etc.).

---

## Caveats and edge cases

- **DISC has lower academic rigor than Big Five or MBTI.** The ODAT was developed by Open Psychometrics by selecting items that best discriminated between self-reported DISC types — it's a reasonable open-source instrument, but DISC as a framework has weaker validation than the Big Five. Treat the result as one signal among several.
- **Workplace context matters.** DISC items are workplace/social behavior framings. Users who answer based on their work persona may score differently from how they'd answer based on their personal life. If the result feels off, ask the user which context they were answering from.
- **Ties at the top are common** in 16-item instruments. If two scores are within 1 point, treat the user as a blend rather than picking one arbitrarily.
- **Item 11 ("I just want everyone to be equal")** can be misread as political — the intended construct is interpersonal equality and humility, not political egalitarianism. If the user asks for clarification, say: "Do you tend to downplay your own status or accomplishments around others?"
- **Item 4 ("I am always on the look out for ways to make money")** loads on the Dominance dimension because the ODAT's development found D-types scored higher on it. It's not measuring greed or materialism per se — it's measuring goal-directed, achievement-oriented behavior in a culturally common form.

If the user's dominant and secondary types are very close, treat the result as the user's *primary tuning* but mention both options.
