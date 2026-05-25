# AgentTune

Tuning rules for AI agents — drop into your agent's system prompt to calibrate it to your personality type.

## What this is

Every frontier AI defaults to roughly the same interaction style. (It turns out, when you make them take the MBTI 500 times, 99% come back as INTJ.) That works fine if you happen to be an INTJ. For everyone else, the agent is subtly miscalibrated for how *you* think.

AgentTune flips it: paste a short tuning file matched to your type, and the agent adjusts.

## How to use

1. Find your type. Don't know it? Take the [OEJTS](https://openpsychometrics.org/tests/OEJTS/1.php) — it's free and research-grade.
2. Open the matching file in [`mbti/`](mbti/).
3. Paste its contents into your agent's system prompt (Claude, ChatGPT, Cursor, Gemini — anywhere you can set instructions).
4. Use as normal. The agent will calibrate.

## Types available

### MBTI
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

### Enneagram
- Coming next

## Why this works

Frontier models are trained on roughly the same corpus and shaped by roughly the same RLHF objectives. The "voice" that emerges is consistent — and consistent in one direction. A tuning file is a small but high-leverage intervention: a few hundred words at the top of a system prompt that tells the agent to invert its defaults for users whose preferences differ.

## License

MIT — see [LICENSE](LICENSE). Use, fork, modify, ship in your own product.

## Contributing

Schema and contribution guide coming once the MBTI set is complete. For now: open an issue if you have feedback on the INTJ note (the calibration draft).
