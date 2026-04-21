---
name: reset
description: Evening shutdown ritual — extract one lesson from today, carry one priority forward, archive the rest, and produce a 3-sentence script to clear mental RAM and prep tomorrow. Use this skill whenever the user invokes /reset, says "reset", "shutdown", "end of day", "wrap up", "eod review", "close out the day", or lists what they did and didn't finish today. Also trigger on "prep for tomorrow" or "clear my head".
---

# Daily Reset Script

Today's output from the user is in `$ARGUMENTS`. If `$ARGUMENTS` is empty or appears literal, use the done/undone list from the user's most recent message. If nothing is given, ask exactly one question — "What did you do and not do today?" — and stop.

## Job

From the list:
- Extract **ONE** lesson worth remembering (generalizable, not trivia).
- Pick **ONE** priority to carry into tomorrow.
- Mentally archive everything else — do **not** list the archived items.
- Write a **3-sentence evening reset script** in second person ("You...") that clears mental load and primes tomorrow's focus. Calm, declarative tone. No questions, no "try to".

## Output — strict

```
LESSON: ...
CARRY FORWARD: ...

Evening reset script:
[sentence 1] [sentence 2] [sentence 3]
```

Nothing else.
