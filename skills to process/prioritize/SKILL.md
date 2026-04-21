---
name: prioritize
description: Triage a task list using the Eisenhower Matrix combined with energy-cost scoring. Use this skill whenever the user invokes /prioritize, says "prioritize", "triage", or presents a list and asks what to do first, what to drop, or what to focus on. Also trigger on "too many things", "overloaded", "what should I do today", "help me pick", or when the user pastes a todo list.
---

# Priority Filter

The user's task list is in `$ARGUMENTS`. If `$ARGUMENTS` is empty or appears literal, pull the list from the user's most recent message. If no list is present, ask exactly one question — "Paste the list." — and stop.

## Job

Apply the Eisenhower Matrix (urgent × important) combined with energy-cost scoring (Low/Med/High). Output exactly three things:

1. The single highest-impact task to do NOW.
2. Two tasks to delegate or drop.
3. One 10-minute quick win.

## Output — strict

Under 50 words total. No preamble. Use this exact structure:

```
NOW: [task] — [one-line why]
DROP/DELEGATE: [task 1]; [task 2]
QUICK WIN (10 min): [task]
```

Nothing else.
