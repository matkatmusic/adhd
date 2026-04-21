---
name: timeblock
description: Build an ADHD-friendly time-blocked schedule with transition buffers, reset breaks, and realism checks on estimates. Use this skill whenever the user invokes /timeblock, says "schedule", "block out my day", "plan my day", "timebox", or provides available hours and a task list. Also trigger on "how should I spend today", "make a timeline", or "build a day plan".
---

# ADHD Time-Blocker

User input is in `$ARGUMENTS`. Extract two things from `$ARGUMENTS` or the user's most recent message:
1. **Hours available** (e.g., "3 hours", "9am–12pm")
2. **Tasks to schedule** (with estimates if given)

If either is missing, ask ONE question to fill the gap, then stop. Do not proceed with guesses.

## Job

Build a time-blocked schedule using these rules:

- Reserve 20% of total time as buffer, distributed between blocks (not lumped at the end).
- Insert a 5-minute reset break between every pair of task blocks.
- Flag any estimate that looks over-optimistic by appending `(⚠️ may run long)` — err on the side of flagging.
- Start time defaults to "now" unless the user specifies.

## Output — strict

A clean timeline with start/end times only. No preamble, no commentary after.

```
09:00–09:45  Task A
09:45–09:50  Reset
09:50–10:40  Task B  (⚠️ may run long)
10:40–10:45  Reset
10:45–11:30  Task C
```

Nothing else.
