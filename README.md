# ADHD Executive Function Skills — Claude Code Plugin

Eight slash commands for ADHD-friendly task management, packaged as a Claude Code plugin. Also usable as standalone skills in Claude.ai.

## Commands

| Command                   | Purpose                                                          |
| ------------------------- | ---------------------------------------------------------------- |
| `/decompose`              | Break an overwhelming task into micro-steps                      |
| `/prioritize`             | Triage a task list (Eisenhower + energy cost)                    |
| `/timeblock`              | Build a time-blocked schedule with buffers                       |
| `/decide`                 | Definitive recommendation between two options                    |
| `/focus`                  | Pre-work ritual + distraction protocol                           |
| `/momentum`               | Velocity check + bottleneck + next move                          |
| `/reset`                  | Evening shutdown ritual                                          |
| `/manage-skill-from-url`  | Import/amend a skill from an ADHD self-help URL                  |

Usage pattern: `/<command> <your input>` — e.g. `/decompose write the AuthV6 state machine tests`.

If you invoke a command with no arguments, the skill will ask one focused question and stop. In Claude Code, type `/` to see the full list.

## Install — Claude Code (plugin)

Inside Claude Code, add the marketplace and install the plugin:

```
/plugin marketplace add matkatmusic/adhd
/plugin install adhd@adhd
```

Commands will appear under the `adhd` namespace (e.g. `/adhd:decompose`) or as bare names if no conflict. Type `/` to confirm.

For local development — clone and point Claude Code at the working copy:

```bash
git clone https://github.com/matkatmusic/adhd.git
```

```
/plugin marketplace add ./adhd
/plugin install adhd@adhd
```

## Install — Claude.ai

Requires a paid plan (Pro, Max, Team, or Enterprise) with custom skills enabled.

Upload each skill's `SKILL.md` individually via **Settings → Capabilities → Skills → Upload skill** — one for each of `skills/decide`, `skills/decompose`, `skills/focus`, `skills/momentum`, `skills/prioritize`, `skills/reset`, `skills/timeblock`. (The plugin manifest under `.claude-plugin/` is Claude Code-specific and not used on Claude.ai.)

In any chat, type the command — e.g., `/decompose write the state machine tests`. The skill auto-triggers from the description match. You can also invoke naturally: "decompose: write the tests" or "I'm overwhelmed by writing the tests".

## Adding skills from URLs

`/manage-skill-from-url <url>` fetches an ADHD self-help article and either creates a new skill under `skills/<name>/SKILL.md` or amends an existing one, merging non-destructively. It will ask you to confirm create-vs-amend and the target name before writing.

## Customizing

Each skill is a plain `SKILL.md`. Edit the body to change behavior; edit the `description:` field to change triggers. Keep the `name:` field lowercase with no spaces — that's the slash command.
