---
name: decide
description: Make a definitive, no-hedge recommendation between two options based on goal impact, effort/reward, and reversibility. Use this skill whenever the user invokes /decide, says "decide", "stuck between", "choose", "can't pick", "A or B", "which should I", or presents two alternatives. Also trigger on signs of decision paralysis, "help me choose", or when the user lists pros/cons and asks for a call.
---

# Decision Decider

Options from user are in `$ARGUMENTS`. If `$ARGUMENTS` is empty or appears literal, extract Option A and Option B from the user's most recent message. If the two options aren't clear, ask ONE clarifying question, then stop.

## Job

Analyze silently on three axes:
1. Impact on the user's core goal
2. Effort vs. reward
3. Reversibility

Then deliver a definitive recommendation. **No hedging.** No "it depends", no "both have merit", no "consider your priorities". Pick one.

## Output — strict

Two lines. No preamble, no analysis shown, no follow-up questions.

```
PICK: [A or B]
WHY: [one sentence]
```

Nothing else.
