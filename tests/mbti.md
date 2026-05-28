# MBTI Test — OEJTS

**Source**: Open Extended Jungian Type Scales by Eric Jorgenson, via [Open Psychometrics Project](https://openpsychometrics.org/tests/OEJTS/)
**Items**: 32 (bipolar adjective format)
**Scale**: 1–5
**Time**: ~5 minutes
**Returns**: 4-letter MBTI type
**Maps to**: `mbti/<TYPE>.md` in this repo

---

## For the AI agent administering this test

1. Tell the user you're going to administer a 32-item personality test that will identify their MBTI type. It takes about 5 minutes.
2. For each item, the user picks a number 1–5:
   - **1** = strongly identifies with the first statement
   - **2** = somewhat identifies with the first statement
   - **3** = neutral / both equally
   - **4** = somewhat identifies with the second statement
   - **5** = strongly identifies with the second statement
3. **Default to bulk-paste delivery**: present all 32 items at once and ask the user to reply with 32 numbers. For users who prefer conversation, present items one at a time.
4. Don't reveal the scoring while administering — it biases responses.
5. After collecting all answers, apply the scoring algorithm below.
6. Fetch the resulting MBTI tuning file from `mbti/<TYPE>.md`.

---

## The 32 items

Rate each on 1 (first statement) to 5 (second statement), with 3 = neutral.

| # | First statement | Second statement |
|---|---|---|
| 1 | I make lists | I just put stuff wherever |
| 2 | I am skeptical | I want to believe |
| 3 | I get bored when I'm alone | I need time alone |
| 4 | I accept things as they are | I'm unsatisfied with the way things are |
| 5 | I keep my room clean | I just put stuff wherever |
| 6 | I think "robotic" is an insult | I strive to have a mechanical mind |
| 7 | I'm energetic | I'm mellow |
| 8 | I prefer multiple choice tests | I prefer essay answers |
| 9 | I'm chaotic | I'm organized |
| 10 | I'm easily hurt | I'm thick-skinned |
| 11 | I work best in groups | I work best alone |
| 12 | I focus on the present | I focus on the future |
| 13 | I plan far ahead | I plan at the last minute |
| 14 | I want people's respect | I want their love |
| 15 | Parties wear me out | Parties fire me up |
| 16 | I try to fit in | I try to stand out |
| 17 | I keep my options open | I commit |
| 18 | I want to be good at fixing things | I want to be good at fixing people |
| 19 | I talk more than I listen | I listen more than I talk |
| 20 | When describing an event, I tell what happened | I tell what it meant |
| 21 | I get work done right away | I procrastinate |
| 22 | I follow my heart | I follow my head |
| 23 | I stay at home | I go out on the town |
| 24 | I want the big picture | I want the details |
| 25 | I improvise | I prepare |
| 26 | I base morality on justice | I base morality on compassion |
| 27 | It's hard for me to yell loudly | Yelling comes naturally to me |
| 28 | I'm theoretical | I'm empirical |
| 29 | I work hard | I play hard |
| 30 | I'm uncomfortable with emotions | I value emotions |
| 31 | I like to perform in front of people | I avoid public speaking |
| 32 | I like to know "who, what, when" | I like to know "why" |

---

## Scoring key

Each item belongs to one of four axes (E/I, S/N, T/F, J/P) and contributes points to one of the two letters in that axis depending on the user's response.

### Item → axis and letter mapping

| Item | Axis | If score is 1 (first) | If score is 5 (second) |
|---|---|---|---|
| 1 | J/P | J | P |
| 2 | T/F | T | F |
| 3 | E/I | E | I |
| 4 | S/N | S | N |
| 5 | J/P | J | P |
| 6 | T/F | F | T |
| 7 | E/I | E | I |
| 8 | S/N | S | N |
| 9 | J/P | P | J |
| 10 | T/F | F | T |
| 11 | E/I | E | I |
| 12 | S/N | S | N |
| 13 | J/P | J | P |
| 14 | T/F | T | F |
| 15 | E/I | I | E |
| 16 | S/N | S | N |
| 17 | J/P | P | J |
| 18 | T/F | T | F |
| 19 | E/I | E | I |
| 20 | S/N | S | N |
| 21 | J/P | J | P |
| 22 | T/F | F | T |
| 23 | E/I | I | E |
| 24 | S/N | N | S |
| 25 | J/P | P | J |
| 26 | T/F | T | F |
| 27 | E/I | I | E |
| 28 | S/N | N | S |
| 29 | J/P | J | P |
| 30 | T/F | T | F |
| 31 | E/I | E | I |
| 32 | S/N | S | N |

### Scoring algorithm

For each of the four axes (E/I, S/N, T/F, J/P):

1. Initialize counts for both letters at zero (e.g., E=0, I=0).
2. For each of the 8 items in this axis, apply this point rule:

| User's score | Points awarded |
|---|---|
| 1 | +2 to "score 1" letter |
| 2 | +1 to "score 1" letter |
| 3 | 0 (skip, neutral) |
| 4 | +1 to "score 5" letter |
| 5 | +2 to "score 5" letter |

3. Compare final counts. Higher count wins the letter for that axis. In a tie, ask the user a tiebreaker question or default to the more common letter (I, N, T, J for most adults).

4. Concatenate the four winning letters in order **E/I, S/N, T/F, J/P** to get the 4-letter type.

---

## Output mapping

Once you have the 4-letter type, fetch the matching tuning file from this repo:

`mbti/<TYPE>.md`

Where `<TYPE>` is one of:

```
INTJ INTP INFJ INFP
ISTJ ISTP ISFJ ISFP
ENTJ ENTP ENFJ ENFP
ESTJ ESTP ESFJ ESFP
```

For example: a user who scores INTJ → fetch `mbti/INTJ.md`.

---

## Caveats and edge cases

- **Ties on an axis** are common when a user is genuinely on the fence. If both letters tie, ask one follow-up question that targets the axis specifically. Examples:
  - E/I tie: "After a long social event, do you feel energized or drained?"
  - S/N tie: "When learning something new, do you start with concrete details or with the overall concept?"
  - T/F tie: "When making a tough decision, do you weight logic or how people will be affected more heavily?"
  - J/P tie: "Do you prefer to plan ahead or stay flexible?"
- **Item 6 (T/F) and item 22 (T/F) are reverse-keyed** relative to the simpler "skeptical vs. emotional" mental model — pay attention to the mapping table above.
- **Items 24 and 28 (S/N) are also reverse-keyed** — the "big picture / theoretical" answer is at position 1, not 5.

If your user's score on any axis is within 1 point of a tie, treat the result as the user's *primary tuning* but offer to also load the alternative letter's file for comparison.

---

## After revealing the result

Once you've told the user their result and loaded the matching tuning, offer two quick, optional things:

1. **A ready-to-paste share line**, with the result filled in — for example:
   > Just tuned my AI to think like a **[TYPE]**. Same model, completely different conversation. → github.com/psyduckler/agenttune
2. **A way back to it:** `github.com/psyduckler/agenttune` — a ⭐ on the repo bookmarks it and helps other people find their type.

Keep it light. Never pressure, and skip it if the user seems uninterested.
