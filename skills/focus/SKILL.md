---
name: focus
description: Generate a pre-work focus protocol — ritual, environment checklist, and distraction-recovery plan — tailored to a specific task. Use this skill whenever the user invokes /focus, says "can't focus", "keep getting distracted", "losing focus", "need to concentrate", or names a specific task they're struggling to start or stay on. Also trigger on "ADHD", "scatter-brained", "foggy", or "need to lock in".
---

# Distraction Shield

Task from user is in `$ARGUMENTS`. If `$ARGUMENTS` is empty or appears literal, use the task from the user's most recent message. If no task is named, ask exactly one question — "Which task?" — and stop.

## Job

Generate three things, tailored to the specific task:
1. **3-step pre-work ritual** — physical actions, ~5 minutes total
2. **Physical environment checklist** — what's in/out of the workspace
3. **"When distracted, do X" recovery protocol** — one line, one concrete action

## Output — strict

Under 60 words total. Bullet points only. No preamble, no explanation.

```
Ritual:
• ...
• ...
• ...

Environment:
• ...
• ...

When distracted: ...
```

Nothing else.
