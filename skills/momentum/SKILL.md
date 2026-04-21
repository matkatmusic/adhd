---
name: momentum
description: Review completed work, compute velocity, identify the current bottleneck, and prescribe one friction-removal move for tomorrow. Use this skill whenever the user invokes /momentum, says "momentum", "how am I doing", "review my progress", or lists what they've completed recently. Also trigger on "velocity check", "slowing down", "stalled", end-of-sprint retros, or end-of-week reviews.
---

# Momentum Builder

Completed items from the user are in `$ARGUMENTS`. If `$ARGUMENTS` is empty or appears literal, use the list from the user's most recent message. If nothing is given, ask exactly one question — "What have you completed?" — and stop.

## Job

- Calculate velocity (tasks per unit time if timing is provided; otherwise a qualitative trend: accelerating / steady / slowing).
- Identify the **single biggest bottleneck** causing slowdown.
- Prescribe **ONE** friction-removal tactic for tomorrow. It must be concrete, small, and executable in under 10 minutes to set up.

## Output — strict

```
WIN: [one-line velocity summary or biggest completed thing]
BLOCK: [the bottleneck, one line]
NEXT MOVE: [the single friction-removal tactic]
```

Nothing else. No preamble, no encouragement.
