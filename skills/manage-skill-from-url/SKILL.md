---
name: manage-skill-from-url
description: Fetch ADHD self-help material from a URL and either create a new skill or amend an existing one in this plugin. Use when the user provides a URL (article, blog post, transcript, guide) containing ADHD strategies they want captured as a reusable skill.
allowed-tools: WebFetch Read Write Edit Glob Bash
argument-hint: <url> [optional skill name or hint]
---

You are extending the `adhd` Claude Code plugin with material from a user-supplied URL.

Arguments: `$ARGUMENTS` — the first token is the URL; anything after is a user hint about desired skill name or scope.

## Step 1 — Fetch the material

Use WebFetch on the URL with a prompt such as:

> "Extract the practical ADHD self-help strategies, coping techniques, mental models, and actionable advice from this page. Preserve concrete steps, scripts, and examples. Ignore boilerplate, ads, and author bios."

If WebFetch is blocked or returns thin content, tell the user and stop — do not fabricate material.

## Step 2 — Decide: create new skill vs amend existing

1. Glob `${CLAUDE_PLUGIN_ROOT}/skills/*/SKILL.md`.
2. Read the frontmatter `description` of each existing skill (skip this one).
3. Judge topical overlap with the fetched material:
   - Strong overlap (same core technique or domain, e.g. both about time-blindness) → propose **amend**.
   - Weak or no overlap → propose **create**.
4. Briefly tell the user: the candidate action, the target skill name, and a 1-sentence rationale. Ask them to confirm before writing. Respect their override.

## Step 3a — Create a new skill

- Pick a short kebab-case name (e.g. `time-blindness`, `task-initiation`, `body-doubling`, `rejection-sensitivity`). Use the user's hint if supplied.
- Create `${CLAUDE_PLUGIN_ROOT}/skills/<name>/SKILL.md` with:

```
---
name: <name>
description: <what the skill covers AND when Claude should use it — one or two sentences, trigger-oriented>
---

<body: actionable instructions for Claude, organized into numbered steps or short sections. Focus on what to DO when helping the user with this ADHD challenge.>

## Sources
- <URL> — <short title or publisher>
```

Constraints on the body:
- Write instructions to Claude, not prose to the user.
- Concrete steps and scripts over theory.
- Keep it tight — aim for signal-dense, not exhaustive.

## Step 3b — Amend an existing skill

1. Read the target `SKILL.md` in full.
2. Identify strategies/techniques in the fetched material that are **not already covered**.
3. Merge non-destructively:
   - Add new strategies as new bullets or sections under the most relevant existing heading, or append a new section if none fits.
   - Refine existing wording only where the new source is clearer, and only with user approval — show a diff/summary first.
   - Append the new URL to a `## Sources` section (create the section if absent).
4. Preserve the existing frontmatter unless the user asks to update the `description`. If you do update it, keep it trigger-oriented.

## Step 4 — Report

After writing, output:
- Path(s) changed.
- A one-paragraph summary of what was added or amended.
- Reminder: run `/plugin` → reload, or restart Claude Code, so the new/updated skill is picked up.

## Guardrails

- Never overwrite a `SKILL.md` without showing the user a summary of the change first.
- Never invent ADHD techniques the source does not actually contain.
- Keep YAML frontmatter valid (no unescaped colons in values, no tabs).
- If the URL points to something unrelated to ADHD self-help, stop and ask the user how to proceed.
